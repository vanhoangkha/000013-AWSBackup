---
title : "Introduction"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 1. </b> "
---

#### Overview

In this exercise, you will become familiar with using **AWS Backup** to create a backup plan for active resources on AWS such as EBS Volumes, RDS Databases, DynamoDB Tables , or EFS File Systems. At the same time, you will also learn how to restore data from backups and automate the whole process.

For many organizations, the data they own is one of the most valuable assets they have. Regular data backups are vital to the long-term success of any organization. However, a data backup is only valid if the data can be restored/restored from the backup. In the cloud, data backup and recovery testing is easier than in on-premises data centers. Automating this process with appropriate notification systems will ensure that an organization's data is backed up regularly, backups are checked to ensure expected recovery, and the right people notified in the event of an error.

![AWS Backup](/images/0/architecture.jpeg?featherlight=false&width=60pc)

#### Target

- Create Backup Plan for the system to automate the backup.
- Test backup/restore operation.
- Test notifications when processes are complete.

#### AWS Backup

**AWS Backup** is an AWS-managed data protection service that allows you to centralize and automate data protection for AWS resources in the cloud and on-prem. With AWS Backup, you can set up and automate your backup policies and backup plans from a single place.

#### AWS Simple Notification Service (SNS)

**AWS SNS** is a service that allows you to send notifications from publishers to subscribers. Publisher communicates asynchronously with subscribers through a topic. That is, Publisher will send a notification to the topic, then that topic will send that notice to subscribers who are subscribed to that topic.