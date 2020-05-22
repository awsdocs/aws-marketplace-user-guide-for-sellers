# Cost allocation tagging<a name="cost-allocation-tagging-ami-marketplace"></a>

AWS Marketplace supports cost allocation tagging for AMI\-based software products\. New and existing Amazon EC2 instance tags will automatically populate against corresponding AWS Marketplace AMI usage\. You can use activated cost allocation tags to identify and track AMI usage through Cost Explorer, the AWS Cost and Usage report, AWS Budgets or other cloud spend analysis tools\.

You can use tags to organize your resources, and cost allocation tags to track your AWS costs on a detailed level\. After you activate cost allocation tags, AWS uses the cost allocation tags to organize your resource costs on your cost allocation report, to make it easier for you to categorize and track your AWS costs\.

Cost allocation tagging will only track costs from the point in time when the tags where activated in the Billing and Cost Management console\. Only AWS account owners, AWS Organizations master account owners, and IAM users with the appropriate permissions can access the Billing and Cost Management console for an account\. There's no change to how much you're billed when using or not using cost allocation tagging\. Using or not using cost allocation tags has no impact on the functionality of your AMI\-based software products\.

## Tracking cost allocation tags for one AMI across multiple instances<a name="multi-instances-cost-allocation-tagging-marketplace"></a>

Each launched Amazon EC2 instance for a AWS Marketplace AMI subscription has a corresponding AWS Marketplace software usage line item in the AWS Cost and Usage report\. Your AWS Marketplace usage will always reflect the specific tags applied to the corresponding Amazon EC2 instance\. This allows you to distinguish your AWS Marketplace usage costs based on the different tag values that were assigned, at an instance level\.

You can also sum up your tag\-based usage costs to equal the AMI software usage charge reflected in your bill with either the Cost Explorer or the AWS Cost and Usage report\.

## Finding budgets with cost allocated tagged instances<a name="cost-allocation-tag-script-marketplace"></a>

If you already have active budgets filtered on cost allocation tags over a number of Amazon EC2 instances in the Billing and Cost Management console, it might be difficult to find all of them\. The following Python script returns a list of budgets which contain Amazon EC2 instances from the AWS Marketplace in your current AWS Region\.

You can use this script to be aware of a potential impact to your budget, and where overruns might occur from this change\. Note that the billed amount doesn't change, but the cost allocations will be reflected more accurately, which can impact budgets\.

```
#! /usr/bin/python

import boto3

session = boto3.Session()
b3account=boto3.client('sts').get_caller_identity()['Account']
print("using account {} in region {}".format(b3account,session.region_name))


def getBudgetFilters(filtertype):
    ''' 
    Returns budgets nested within the filter values [filter value][budeget name].
    The filtertype is the CostFilter Key such as Region, Service, TagKeyValue.
    '''    
    budget_client = session.client('budgets')
    budgets_paginator = budget_client.get_paginator('describe_budgets')
    budget_result = budgets_paginator.paginate(
        AccountId=b3account
    ).build_full_result()    
    returnval = {}
    if 'Budgets' in budget_result:
        for budget in budget_result['Budgets']:
            for cftype in budget['CostFilters']:
                if filtertype == cftype:                          
                    for cfval in budget['CostFilters'][cftype]:
                        if cfval in returnval:
                            if not budget['BudgetName'] in returnval[cfval]:
                                returnval[cfval].append(budget['BudgetName'])
                        else:
                            returnval[cfval] = [ budget['BudgetName'] ]
    return returnval

def getMarketplaceInstances():
    '''
    Get all the AWS EC2 instances which originated with AWS Marketplace.        
    '''
    ec2_client = session.client('ec2')
    paginator = ec2_client.get_paginator('describe_instances')
    returnval = paginator.paginate(
        Filters=[{
            'Name': 'product-code.type',
            'Values': ['marketplace']
        }]
    ).build_full_result()
    return returnval


def getInstances():
    mp_instances = getMarketplaceInstances()
    budget_tags = getBudgetFilters("TagKeyValue")
    cost_instance_budgets = []
    for instance in [inst for resrv in mp_instances['Reservations'] for inst in resrv['Instances'] if 'Tags' in inst.keys()]:    
        for tag in instance['Tags']:                
            # combine the tag and value to get the budget filter string
            str_full = "user:{}${}".format(tag['Key'], tag['Value'])
            if str_full in budget_tags:
                for budget in budget_tags[str_full]:
                    if not budget in cost_instance_budgets:
                        cost_instance_budgets.append(budget)    
    print("\r\nBudgets containing tagged Marketplace EC2 instances:")
    print( '\r\n'.join([budgetname for budgetname in cost_instance_budgets]) )


if __name__ == "__main__":
    getInstances()
```

**Example output**

```
Using account 123456789012 in region us-east-2

Budgets containing tagged Marketplace EC2 instances:
EC2 simple
MP-test-2
```

## Related topics<a name="cost-allocation-tagging-related-topics"></a>

For more information, see the following links:
+ [Using Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html) in the *AWS Billing and Cost Management User Guide*\. 
+ [Activating the AWS\-Generated Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/activate-built-in-tags.html) in the *AWS Billing and Cost Management User Guide*\. 
+ [Tagging Your Amazon EC2 Resources](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html) in the Amazon EC2 User Guide for Linux Instances\.