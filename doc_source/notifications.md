# Notifications for AWS Marketplace events<a name="notifications"></a>

The AWS Marketplace Notifications team can send automated email messages to the address associated with your AWS account to provide visibility into events on AWS Marketplace\. You do not need to set up notifications they are sent automatically for all AWS Marketplace product type subscriptions\.

The AWS Marketplace Notifications team sends email notifications for offers and agreements made in AWS Marketplace verifying the transaction\. The notifications are sent in real\-time based on the successful fulfilment of a customer subscription\. 

As a seller, you will receive an email notification when a buyer accepts an offer\. As a buyer, you will receive an email notification when you accept an offer\. Notifications are sent to a buyer and an Independent Software Vendor \(ISV\) for public or private offers subscriptions\. They are also sent to a buyer, ISV, and channel partner for Consulting Partner Private Offers \(CPPO\) private offer subscriptions\.

Email notifications contain details listed here \(to ISV and CP\):
+ Purchase date, time, and time zone
+ Customer AWS account ID
+ Product name
+ Product identification
+ Offer name
+ Offer identification
+ Agreement identification
+ Service start date
+ Service end date
+ Purchase amount \(for contract and CCP\)

AWS Marketplace can also send notifications through Amazon Simple Notification Service \(Amazon SNS\) about changes to customers' subscriptions and contract entitlements for the following products:
+ [Amazon SNS notifications for SaaS products](saas-notification.md)
+ [Amazon SNS notifications for AMI products](ami-notification.md)
+ [Amazon SNS notifications for container products](container-notification.md)

The following topics describe the event types that are supported by email notifications and how to manage notifications:

**Topics**
+ [Event types](#event-types)
+ [Manage notifications](#manage-notifications)

## Event types<a name="event-types"></a>

The following event types are supported by email notifications for all products and pricing types:
+ Buyer has requested a professional service product
+ Recurring scan vulnerability or recurring scan reminder
+ Reseller opportunity has been created, updated, or expired 
+ Consulting partner private offer has been published
+ Email notifications to buyer and seller for offer acceptance

  For more information about reseller opportunities for consulting partner private offers, see [Creating a resell opportunity for a consulting partner as an ISV](consulting-partner-isv-info.md) and [Creating a private offer as a consulting partner](consulting-partner-info.md)\.

## Manage notifications<a name="manage-notifications"></a>

The following topics explain how to manage email notifications for events:

**Topics**
+ [Adding or updating email addresses](#adding-email-address)
+ [Unsubscribing recipients from notifications](#unsubscribe)

### Adding or updating email addresses<a name="adding-email-address"></a>

You can add up to 10 email addresses for custom email notifications using the AWS Marketplace Management Portal\.

**To add or update email addresses**

1. Sign in to the [AWS Marketplace Management Portal\.](https://aws.amazon.com/marketplace/management/)

1. From **Settings**, choose the **Notifications** tab\.

1. Under **Email for custom notifications**, choose **Add email address**\.

1. For **Recipient details,** enter a custom email address in the **Email address** field\.

1. \(Optional\) Choose **Add new recipients** to add another email address \(up to 10 total\)\.

1. Choose **Submit**\.

### Unsubscribing recipients from notifications<a name="unsubscribe"></a>

You can remove an email address so the recipient is unsubscribed from custom email notifications\.

**To unsubscribe recipients from event notifications**

1. Sign in to the [AWS Marketplace Management Portal\.](https://aws.amazon.com/marketplace/management/) 

1. From **Settings** choose the **Notifications** tab\.

1. Under **Email for custom notifications**, choose **Update email address**\.

1. For **Recipient details**, choose **Remove** to remove the email address\.

1. Choose **Submit**\.

   The recipient will no longer receive email notifications for custom events\.