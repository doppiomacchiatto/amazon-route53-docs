# Editing Resource Record Sets<a name="resource-record-sets-editing"></a>

The following procedure explains how to edit resource record sets using the Amazon Route 53 console\. For information about how to edit resource record sets using the Amazon Route 53 API, see [ChangeResourceRecordSets](http://docs.aws.amazon.com/Route53/latest/APIReference/API_ChangeResourceRecordSets.html) in the *Amazon Route 53 API Reference*\.

**Note**  
Your changes to resource record sets take time to propagate to the Amazon Route 53 DNS servers\. Currently, the only way to verify that changes have propagated is to use the [GetChange](http://docs.aws.amazon.com/Route53/latest/APIReference/API_GetChange.html) API action\. Changes generally propagate to all Amazon Route 53 name servers within 60 seconds\.

**To edit resource record sets using the Amazon Route 53 console**

1. If you're not editing alias resource record sets, skip to step 2\. 

   If you're editing alias resource record sets that route traffic to ELB Classic, Application, or Network Load Balancers, and if you created your Amazon Route 53 hosted zone and your load balancer using different accounts, perform the procedure [Getting the DNS Name for an ELB Load Balancer](resource-record-sets-creating.md#resource-record-sets-elb-dns-name-procedure) to get the DNS name for the load balancer\. 

   If you're editing alias resource record sets for any other AWS resource, skip to step 2\.

1. Sign in to the AWS Management Console and open the Amazon Route 53 console at [https://console\.aws\.amazon\.com/route53/](https://console.aws.amazon.com/route53/)\.

1. On the **Hosted Zones** page, double\-click the row for the hosted zone in which you want to edit resource record sets\.

1. Double\-click the row for the resource record set that you want to edit\. 

1. Enter the applicable values\. For more information, see [Values That You Specify When You Create or Edit Amazon Route 53 Records](resource-record-sets-values.md)\. 

1. Click **Save Record Set**\.

1. If you're editing multiple resource record sets, repeat steps 4 through 6\.