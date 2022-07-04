---
title : "Tạo Backup plan"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

####  Tạo Backup plan

Một chiến lược dự phòng được suy nghĩ kỹ lưỡng là chìa khóa dẫn đến thành công của một tổ chức và được xác định bởi nhiều yếu tố. Các yếu tố lớn nhất ảnh hưởng đến chiến lược sao lưu là Mục tiêu thời gian khôi phục (RTO) và Mục tiêu điểm khôi phục (RPO) được đặt cho khối lượng công việc. RTO và RPO được xác định dựa trên mức độ quan trọng của khối lượng công việc đối với doanh nghiệp, SLA đã được thỏa thuận và chi phí liên quan đến việc đạt được RTO và RPO. RTO và RPO phải cụ thể cho từng khối lượng công việc và không được đặt cho toàn bộ tổ chức / cơ sở hạ tầng.

Trong phòng thí nghiệm này, bạn sẽ tạo một chiến lược sao lưu bằng cách tận dụng AWS Backup, một dịch vụ sao lưu được quản lý hoàn toàn có thể tự động sao lưu dữ liệu từ các nguồn dữ liệu khác nhau như EC2, EBS, Cơ sở dữ liệu RDS, v.v. Bạn có thể xem danh sách đầy đủ các dịch vụ được hỗ trợ tại [đây](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html#supported-resources).

1. Truy cập vào **AWS Management Console**

   - Truy cập vào **AWS Management Console**
   - Tìm và chọn **AWS Backup**

![AWS Backup](/images/3/0001.png?featherlight=false&width=90pc)

2. Chọn **AWS Backup Plan**

![AWS Backup](/images/3/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create backup plan**, chọn **Build a new plan**

   - Đối với **Backup plan name**, nhập **```BACKUP-LAB```**
   - Đối với **SCHEDULE**, phần **FREQUENCY**, chọn **Daily**


![AWS Backup](/images/3/0003.png?featherlight=false&width=90pc)

4. Trong phần **BACKUP RULE CONFIGURATION**

   - Nhập **RULE NAME** là **BACKUP-LAB-RULE**
   - Chọn mặc định **Use backup window defaults - recommended**
   - Đối với **BACKUP VAULT**, chọn **CREATE NEW BACKUP VAULT**

![AWS Backup](/images/3/0004.png?featherlight=false&width=90pc)

5. Đối với **BACKUP VAULT NAME**, nhập  **BACKUP-LAB-VAULT.**

   - Chọn **(default) aws/backup.**
   - Chọn **CREATE BACKUP VAULT**

![AWS Backup](/images/3/0005.png?featherlight=false&width=90pc)

6. Thêm **Key** và **Value** của tag.

   - Chọn **Create plan**

![AWS Backup](/images/3/0006.png?featherlight=false&width=90pc)

7. Hoàn thành tạo **Backup plan**

   - Trong phần **RESOURCE ASSIGNMENTS**, chọn **ASSIGN RESOURCES.**

![AWS Backup](/images/3/0007.png?featherlight=false&width=90pc)

8. Đối với **RESOURCE ASSIGNMENT NAME**, nhập **BACKUP-RESOURCES**

   - Chọn **DEFAULT ROLE** đối với **IAM ROLE**. Nếu role không tồn tại, AWS Backup sẽ tạo 1 role mới với permission cần thiết. 
   - Sau đó thêm **Tag Key** và **Tag Value**
   - Chọn **ASSIGN RESOURCES**

![AWS Backup](/images/3/0008.png?featherlight=false&width=90pc)

9. Xác nhận chọn *Continue**

![AWS Backup](/images/3/0009.png?featherlight=false&width=90pc)

10. Hoàn thành **ASSIGN RESOURCES**

![AWS Backup](/images/3/00010.png?featherlight=false&width=90pc)


