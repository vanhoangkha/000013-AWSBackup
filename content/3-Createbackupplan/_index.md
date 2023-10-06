---
title : "Create Backup plan"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Create Backup Plan

A well-thought-out contingency strategy is key to an organization's success and is determined by many factors. The most significant factors influencing backup strategy are the Recovery Time Objective (RTO) and Restore Point Objective (RPO) set for the workload. RTOs and RPOs are determined based on how important the workload is to the business, the agreed SLA, and the costs involved in achieving the RTO and RPO. RTOs and RPOs should be specific to each workload and should not be set for the entire organization/infrastructure.

In this lab, you will create a backup strategy by leveraging AWS Backup, a fully managed backup service that can automatically back up data from different data sources such as EC2, EBS, RDS Database, etc. A full list of supported services can be found [here](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html#supported-resources).

1. Go to **AWS Management Console**

   - Access the **AWS Management Console**
   - Find and select **AWS Backup**

![AWS Backup](/images/3-backupplan/1.png?featherlight=false&width=90pc)

2. Select **AWS Backup Plan**

![AWS Backup](/images/3-backupplan/2.png?featherlight=false&width=90pc)

3. In the **Create backup plan** interface, select **Build a new plan**

   - For the **Backup plan name**, enter **`BACKUP-LAB`**

![AWS Backup](/images/3-backupplan/3.png?featherlight=false&width=90pc)

4. In the **BACKUP RULE CONFIGURATION** section

   - Enter **RULE NAME** as **`BACKUP-LAB-RULE`**
   - For the **SCHEDULE** and **FREQUENCY** section, select **Daily**
   - Select the default **Use backup window defaults - recommended**
   - For the **BACKUP VAULT**, select **CREATE NEW BACKUP VAULT**

![AWS Backup](/images/3-backupplan/4.png?featherlight=false&width=90pc)

5. For the **BACKUP VAULT NAME**, enter **`BACKUP-LAB-VAULT`**

   - Select **(default) aws/backup.**
   - Select **CREATE BACKUP VAULT**

![AWS Backup](/images/3-backupplan/5.png?featherlight=false&width=90pc)

6. Add **Key** and **Value** for the tag.

   - Select **Create plan**

![AWS Backup](/images/3-backupplan/6.png?featherlight=false&width=90pc)

7. Finish creating the **Backup plan**

   - In the **RESOURCE ASSIGNMENTS** section, select **ASSIGN RESOURCES.**

![AWS Backup](/images/3-backupplan/7.png?featherlight=false&width=90pc)

8. For the **RESOURCE ASSIGNMENT NAME**, enter **`BACKUP-RESOURCES`**

   - Select the **DEFAULT ROLE** for the **IAM ROLE**. If the role does not exist, AWS Backup will create a new role with the necessary permissions.
   - Then add the **Tag Key** and **Tag Value**
   - Select **ASSIGN RESOURCES**

![AWS Backup](/images/3-backupplan/8.png?featherlight=false&width=90pc)

9. Confirm your selection and click **Continue**

![AWS Backup](/images/3-backupplan/9.png?featherlight=false&width=90pc)

10. Complete the **ASSIGN RESOURCES**

![AWS Backup](/images/3-backupplan/10.png?featherlight=false&width=90pc)
