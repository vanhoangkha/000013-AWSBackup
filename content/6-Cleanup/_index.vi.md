---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Dọn dẹp tài nguyên


#### Xóa SNS Subscriber

- Truy cập vào AWS SNS Console
- Chọn Subscription ở thanh bên trái
- Chọn và xóa các Subscriber liên quan

#### Xóa SNS Topic

- Truy cập vào AWS SNS Console
- Chọn Topics ở thanh bên trái
- Chọn và xóa Topic liên quan

#### Xóa Backup Vaults

- Truy cập vào AWS Backup Console
- Chọn Backup Vaults ở thanh bên trái
- Chọn Backup Vault được tạo trong bài này
- Ở mục Backups, tick vào backup đã tạo, chọn Actions, và chọn Delete
- Ở trang thông tin Backup Vault, chọn Delete

#### Xóa Backup Plans

- Truy cập vào AWS Backup Console
- Chọn Backup plans ở thanh bên trái
- Chọn Backup plan được tạo trong bài này
- Ở mục Resource assignments, chọn resource đã tạo và chọn Delete
- Ở trang thông tin Backup plan, chọn Delete

#### Xóa CloudFormation Stack

- Truy nhập vào **AWS CloudFormation**
- Chọn **Stack** của bài lab.
- Chọn **Delete**

#### Xóa CloudWatch Logs

- Truy nhập vào **AWS CloudWatch**
- Chọn **Logs**
- Chọn **/aws/lambda/RestoreTestFunction.**
- Chọn **Actions**, chọn **Delete Log Group**
- Chọn **Yes, Delete**

