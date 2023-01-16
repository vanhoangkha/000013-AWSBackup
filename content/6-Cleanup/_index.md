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

![Clean](/images/6-clean/2.png?featherlight=false&width=90pc)

#### Delete Backup Vaults

- Access to AWS Backup Console
- Select Backup Vaults in the left sidebar
- Select Backup Vault created in this post

![Clean](/images/6-clean/3.png?featherlight=false&width=90pc)

- Detail Backup Vault
- In section **Recovery points**, click  **Recovery points**, choose Actions then Delete


![Clean](/images/6-clean/4.png?featherlight=false&width=90pc)


- Next on section Backups **Delete vault**

![Clean](/images/6-clean/6.png?featherlight=false&width=90pc)

![Clean](/images/6-clean/5.png?featherlight=false&width=90pc)
#### Delete Backup Plans

- Access to AWS Backup Console
- Select Backup plans in the left sidebar
- Select the Backup plan created in this post

![Clean](/images/6-clean/7.png?featherlight=false&width=90pc)

- In the Resource assignments section, select the created resource and select Delete


![Clean](/images/6-clean/8.png?featherlight=false&width=90pc)

- On the Backup plan information page, select Delete

![Clean](/images/6-clean/9.png?featherlight=false&width=90pc)

#### Clear CloudFormation Stack

- Access to **AWS CloudFormation**
- Select **Stack** of the lab.
- Select **Delete**

![Clean](/images/6-clean/10.png?featherlight=false&width=90pc)

#### Clear CloudWatch Logs

- Access to **AWS CloudWatch**
- Select **Logs**
- Select **/aws/lambda/RestoreTestFunction.**
- Select **Actions**, select **Delete Log Group**
- Select **Yes, Delete**

![Clean](/images/6-clean/11.png?featherlight=false&width=90pc)