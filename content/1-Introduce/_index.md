---
title : "Introduction"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 1. </b> "
---

#### Overview

In this exercise, you will become familiar with using **AWS Backup** to create a backup plan for active resources on AWS such as EBS Volumes, RDS Databases, DynamoDB Tables, or EFS File Systems. You will also learn how to restore data from backups and automate the entire process.

For many organizations, the data they own is one of the most valuable assets. Regular data backups are vital for the long-term success of any organization. However, a data backup is only valuable if the data can be successfully restored from it. In the cloud, data backup and recovery testing is easier compared to on-premises data centers. Automating this process with appropriate notification systems ensures that an organization's data is regularly backed up, backups are validated for expected recovery, and the right people are notified in case of errors.

![AWS Backup](/images/0/architecture.jpeg?featherlight=false&width=60pc)

#### Target

- Create a Backup Plan to automate the backup system.
- Test backup and restore operations.
- Test notifications upon completion of processes.

#### AWS Backup

**AWS Backup** is an AWS-managed data protection service that centralizes and automates data protection for AWS resources, both in the cloud and on-premises. With AWS Backup, you can establish and automate backup policies and plans from a single location.

#### AWS Simple Notification Service (SNS)

**AWS SNS** is a service enabling the sending of notifications from publishers to subscribers. Publishers communicate asynchronously with subscribers through topics. In other words, a publisher sends a notification to a topic, which then relays the notice to subscribers subscribed to that topic.
