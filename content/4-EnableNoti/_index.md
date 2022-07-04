---
title : "Notification Settings"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Set up notifications

In the cloud, you can easily set up notifications for events in your workload. AWS Backup leverages AWS SNS to send notifications regarding ongoing backup operations. This will allow visibility of fallback job statuses, rollback job statuses, or any errors that may have occurred, allowing your Operations teams to respond appropriately.

1. Open a Terminal with access to the AWS CLI. Make sure that the CLI is up to date and that you have AWS Administrator Permissions to run AWS CLI commands.

   - Edit the following AWS CLI command and include the ARN of the SNS TOPIC you created. Replace with the SNS TOPIC ARN obtained from the CloudFormation Stack output.
```
aws backup put-backup-vault-notifications --region ap-southeast-1 --backup-vault-name BACKUP-LAB-VAULT --backup-vault-events BACKUP_JOB_COMPLETED RESTORE_JOB_COMPLETED --sns-topic-arn <YOUR SNS TOPIC ARN >
```
   - After editing, run the above command, it will turn on notifications with messages published to SNS TOPIC every time a backup or restore job is done. This will ensure the Operations Team is aware of any errors when backing up or restoring data.

![AWS Backup](/images/4/0001.png?featherlight=false&width=90pc)

2. Check the **SNS** interface

![AWS Backup](/images/4/0002.png?featherlight=false&width=90pc)

3. You can verify that notifications are enabled by running the following command. The output will include a section called SNSTopicArn, followed by the ARN of the generated SNS Topic.

```
aws backup get-backup-vault-notifications --backup-vault-name BACKUP-LAB-VAULT --region ap-southeast-1
```

![AWS Backup](/images/4/0003.png?featherlight=false&width=90pc)

You have now successfully enabled notifications for BACKUP-LAB-VAULT, ensuring that the Operations team is aware of the completion of the backup and restore operations related to this vault and any associated errors. to those activities.