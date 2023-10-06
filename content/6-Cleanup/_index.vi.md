---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

## Dọn dẹp tài nguyên

### Xóa SNS Subscriber

- Truy cập vào AWS SNS Console.
- Chọn Subscription ở thanh bên trái.
- Chọn và xóa các Subscriber liên quan.

![Clean](/images/6-clean/1.png?featherlight=false&width=90pc)

### Xóa SNS Topic

- Truy cập vào AWS SNS Console.
- Chọn Topics ở thanh bên trái.
- Chọn và xóa Topic liên quan.

![Clean](/images/6-clean/2.png?featherlight=false&width=90pc)

### Xóa Backup Vaults

- Truy cập vào AWS Backup Console.
- Chọn Backup Vaults ở thanh bên trái.
- Chọn Backup Vault được tạo trong bài này.

![Clean](/images/6-clean/3.png?featherlight=false&width=90pc)

- Ở trang thông tin Backup Vault.
- Ở mục **Recovery points**, tick vào **Recovery points**, chọn Actions, và chọn Delete.

![Clean](/images/6-clean/4.png?featherlight=false&width=90pc)

- Tiếp theo ở mục Backups khi đã xóa **Recovery points** ta chọn **Delete vault**.

![Clean](/images/6-clean/6.png?featherlight=false&width=90pc)

![Clean](/images/6-clean/5.png?featherlight=false&width=90pc)

### Xóa Backup Plans

- Truy cập vào AWS Backup Console.
- Chọn Backup plans ở thanh bên trái.
- Chọn Backup plan được tạo trong bài này.

![Clean](/images/6-clean/7.png?featherlight=false&width=90pc)

- Ở mục Resource assignments, chọn resource đã tạo và chọn Delete.

![Clean](/images/6-clean/8.png?featherlight=false&width=90pc)

- Ở trang thông tin Backup plan, chọn Delete.

![Clean](/images/6-clean/9.png?featherlight=false&width=90pc)

### Xóa CloudFormation Stack

- Truy nhập vào **AWS CloudFormation**.
- Chọn **Stack** của bài lab.
- Chọn **Delete**.

![Clean](/images/6-clean/10.png?featherlight=false&width=90pc)

### Xóa CloudWatch Logs

- Truy nhập vào **AWS CloudWatch**.
- Chọn **Logs**.
- Chọn **/aws/lambda/RestoreTestFunction.**
- Chọn **Actions**, chọn **Delete Log Group**.
- Chọn **Yes, Delete**.

![Clean](/images/6-clean/11.png?featherlight=false&width=90pc)




