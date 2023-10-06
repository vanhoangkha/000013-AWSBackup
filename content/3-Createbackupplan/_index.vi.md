---
title : "Tạo Backup plan"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

#### Tạo Backup Plan

Để đảm bảo một chiến lược sao lưu hoàn hảo, cần có sự cân nhắc kỹ lưỡng và đa chiều. Thành công của một tổ chức phụ thuộc nhiều yếu tố, trong đó có chiến lược dự phòng. Các yếu tố chủ yếu ảnh hưởng đến chiến lược sao lưu bao gồm Mục tiêu thời gian khôi phục (RTO) và Mục tiêu điểm khôi phục (RPO), mà phải được xác định cho từng khối lượng công việc. RTO và RPO phụ thuộc vào mức độ quan trọng của công việc đối với doanh nghiệp, thỏa thuận về Dịch vụ Mức dịch vụ (SLA) và các yếu tố chi phí liên quan đến việc đạt được RTO và RPO. Chú ý rằng RTO và RPO cần được xác định cụ thể cho từng khối lượng công việc cụ thể, không phải cho toàn bộ tổ chức hoặc cơ sở hạ tầng.

#### Bước 1: Truy cập vào AWS Management Console

- Mở **AWS Management Console**
- Tìm và chọn **AWS Backup**

![Bước 1](/images/3-backupplan/1.png?featherlight=false&width=90pc)

#### Bước 2: Chọn AWS Backup Plan

![Bước 2](/images/3-backupplan/2.png?featherlight=false&width=90pc)

#### Bước 3: Tạo kế hoạch sao lưu

- Trong giao diện **Create backup plan**, chọn **Build a new plan**
- Đối với trường **Backup plan name**, nhập **`BACKUP-LAB`**

![Bước 3](/images/3-backupplan/3.png?featherlight=false&width=90pc)

#### Bước 4: Cấu hình quy tắc sao lưu

- Điền **RULE NAME** là **BACKUP-LAB-RULE**
- Về phần **SCHEDULE**, mục **FREQUENCY**, chọn **Daily**
- Chọn **Use backup window defaults - recommended** để sử dụng cài đặt mặc định cho cửa sổ sao lưu
- Đối với **BACKUP VAULT**, chọn **CREATE NEW BACKUP VAULT**

![Bước 4](/images/3-backupplan/4.png?featherlight=false&width=90pc)

#### Bước 5: Đặt tên cho Backup Vault

- Điền tên **BACKUP VAULT NAME** là **BACKUP-LAB-VAULT**
- Chọn **(default) aws/backup**
- Chọn **CREATE BACKUP VAULT**

![Bước 5](/images/3-backupplan/5.png?featherlight=false&width=90pc)

#### Bước 6: Thêm các cặp Key và Value cho tag

- Chọn **Create plan**

![Bước 6](/images/3-backupplan/6.png?featherlight=false&width=90pc)

### Bước 7: Hoàn tất việc tạo Backup Plan

- Trong phần **RESOURCE ASSIGNMENTS**, chọn **ASSIGN RESOURCES**

![Bước 7](/images/3-backupplan/7.png?featherlight=false&width=90pc)

#### Bước 8: Gán tài nguyên cho Backup Plan

- Điền **RESOURCE ASSIGNMENT NAME** là **BACKUP-RESOURCES**
- Chọn **DEFAULT ROLE** cho **IAM ROLE**. Nếu role không tồn tại, AWS Backup sẽ tự động tạo một role mới với các quyền cần thiết
- Thêm **Tag Key** và **Tag Value**
- Chọn **ASSIGN RESOURCES**

![Bước 8](/images/3-backupplan/8.png?featherlight=false&width=90pc)

#### Bước 9: Xác nhận và tiếp tục

- Xác nhận bằng cách chọn **Continue**

![Bước 9](/images/3-backupplan/9.png?featherlight=false&width=90pc)

#### Bước 10: Hoàn tất việc gán tài nguyên

![Bước 10](/images/3-backupplan/10.png?featherlight=false&width=90pc)


