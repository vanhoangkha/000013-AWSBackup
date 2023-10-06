---
title : "Deploy infrastructure"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---


#### Deploy Infrastructure

In this exercise, you will become familiar with using **AWS Backup** to create a backup plan for active resources on AWS such as EBS Volumes, RDS Databases, DynamoDB Tables, or EFS File Systems. You will also learn how to restore data from backups and automate the entire process.

For many organizations, the data they own is one of the most valuable assets they have. Regular data backups are vital for the long-term success of any organization. However, a data backup is only valid if the data can be successfully restored from the backup. In the cloud, data backup and recovery testing is easier compared to on-premises data centers. Automating this process with appropriate notification systems will ensure that an organization's data is backed up regularly, backups are verified for expected recovery, and the right personnel are notified in the event of an error.

![AWS Backup](/images/0/architecture.jpeg?featherlight=false&width=60pc)

1. Access the **AWS Management Console** interface.

   - Find and select **CloudFormation**.

![AWS Backup](/images/2-preparation/22.png?featherlight=false&width=90pc)

2. Select **Create stack**.

![AWS Backup](/images/2-preparation/23.png?featherlight=false&width=90pc)

3. In the **Create stack** interface:

   - For **PREREQUISITE - PREPARE TEMPLATE**, select **Template is ready**.
   - For **SPECIFY TEMPLATE**, select **Amazon S3 URL**.
   - For **Amazon S3 URL**, enter the URL you created.
   - Select **Next**.

![AWS Backup](/images/2-preparation/24.png?featherlight=false&width=90pc)

4. In the **STACK NAME** section, enter **Backup-plan** (or any desired name).

   - Select **AvailabilityZone**.
   - For **LatestAmiId**, choose the default value.
   - For **NotificationEmail**, enter your email address to receive notifications.
   - For **S3BucketName**, enter the name of the **S3 bucket** you created.
   - For **S3KeyLambdaZip**, enter the path of **lambda_function.zip**.

![AWS Backup](/images/2-preparation/25.png?featherlight=false&width=90pc)

5. In the **CONFIGURE STACK OPTIONS** section, select **Next**.

![AWS Backup](/images/2-preparation/26.png?featherlight=false&width=90pc)

6. For **CAPABILITIES**, select **I acknowledge that AWS CloudFormation might create IAM resources**.

   - Select **Submit**.

![AWS Backup](/images/2-preparation/27.png?featherlight=false&width=90pc)

7. Complete the CloudFormation stack creation.

![AWS Backup](/images/2-preparation/28.png?featherlight=false&width=90pc)

8. Check the **Output** of the CloudFormation stack.

![AWS Backup](/images/2-preparation/29.png?featherlight=false&width=90pc)

9. Select the **Value** of **ApplicationURL**.

![AWS Backup](/images/2-preparation/30.png?featherlight=false&width=90pc)

10. Check your email; you will receive a notification email.

![AWS Backup](/images/2-preparation/31.png?featherlight=false&width=90pc)

11. Perform email confirmation.

![AWS Backup](/images/2-preparation/32.png?featherlight=false&width=90pc)
