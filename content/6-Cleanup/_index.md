---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Clean up resources


#### Delete SNS Subscriber

- Access to AWS SNS Console
- Select Subscription in the left sidebar
- Select and delete related Subscribers

#### Delete SNS Topic

- Access to AWS SNS Console
- Select Topics in the left sidebar
- Select and delete related Topics

#### Delete Backup Vaults

- Access to AWS Backup Console
- Select Backup Vaults in the left sidebar
- Select Backup Vault created in this post
- In the Backups section, tick the created backup, select Actions, and select Delete
- On the Backup Vault information page, select Delete

#### Delete Backup Plans

- Access to AWS Backup Console
- Select Backup plans in the left sidebar
- Select the Backup plan created in this post
- In the Resource assignments section, select the created resource and select Delete
- On the Backup plan information page, select Delete

#### Clear CloudFormation Stack

- Access to **AWS CloudFormation**
- Select **Stack** of the lab.
- Select **Delete**

#### Clear CloudWatch Logs

- Access to **AWS CloudWatch**
- Select **Logs**
- Select **/aws/lambda/RestoreTestFunction.**
- Select **Actions**, select **Delete Log Group**
- Select **Yes, Delete**