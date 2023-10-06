---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

## Clean up resources

### Delete SNS Subscriber

- Access the AWS SNS Console.
- Select "Subscription" in the left sidebar.
- Choose and delete the relevant subscribers.

### Delete SNS Topic

- Access the AWS SNS Console.
- Select "Topics" in the left sidebar.
- Choose and delete the relevant topics.

![Clean](/images/6-clean/2.png?featherlight=false&width=90pc)

### Delete Backup Vaults

- Access the AWS Backup Console.
- Select "Backup Vaults" in the left sidebar.
- Choose the backup vault created in this post.

![Clean](/images/6-clean/3.png?featherlight=false&width=90pc)

- Navigate to the details of the backup vault.
- In the "Recovery points" section, click on "Recovery points," then choose "Actions" and select "Delete."

![Clean](/images/6-clean/4.png?featherlight=false&width=90pc)

- Next, in the "Backups" section, choose "Delete vault."

![Clean](/images/6-clean/6.png?featherlight=false&width=90pc)

![Clean](/images/6-clean/5.png?featherlight=false&width=90pc)

### Delete Backup Plans

- Access the AWS Backup Console.
- Select "Backup plans" in the left sidebar.
- Choose the backup plan created in this post.

![Clean](/images/6-clean/7.png?featherlight=false&width=90pc)

- In the "Resource assignments" section, select the created resource and choose "Delete."

![Clean](/images/6-clean/8.png?featherlight=false&width=90pc)

- On the Backup plan information page, select "Delete."

![Clean](/images/6-clean/9.png?featherlight=false&width=90pc)

### Clear CloudFormation Stack

- Access **AWS CloudFormation**.
- Select the relevant stack from the lab.
- Choose "Delete."

![Clean](/images/6-clean/10.png?featherlight=false&width=90pc)

### Clear CloudWatch Logs

- Access **AWS CloudWatch**.
- Select "Logs."
- Choose **/aws/lambda/RestoreTestFunction**.
- Select "Actions," then choose "Delete Log Group."
- Confirm by selecting "Yes, Delete."

![Clean](/images/6-clean/11.png?featherlight=false&width=90pc)
