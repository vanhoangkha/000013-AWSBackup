+++
title = "Thiết lập Notification"
date = 2020
weight = 3
chapter = false
pre = "<b>3.2. </b>"
+++

Để thiết lập thông báo, chúng ta sẽ sử dụng câu lệnh thông qua AWS CLI. (Bạn có thể tìm hiểu thêm về CLI thông qua [Sử dụng AWS CLI trên Windows/Ubuntu]())

**Nội dung:**
- [Thiết lập Notification](#thiết-lập-notification)

#### Thiết lập Notification

1. Sử dụng Terminal (hoặc Command Prompt trên Windows) để sử dụng AWS CLI.
2. Sử dụng lệnh ```aws backup put-backup-vault-notifications``` để kích hoạt tính năng Notification cho Backup Vault của bạn. Hãy chú ý các thông số truyền vào của câu lệnh.

```bash
aws backup put-backup-vault-notifications --region ap-northeast-1 --backup-vault-name sharenote-backup-vault --backup-vault-events BACKUP_JOB_COMPLETED RESTORE_JOB_COMPLETED --sns-topic-arn arn:aws:sns:ap-northeast-1:340879421878:sharenote-backup-sns
```

  - *--region* : Chọn Region phù hợp mà bạn đang sử dụng (Có thể bỏ qua nếu đã thiết lập Region mặc định)
  - *--backup-vault-name* : Tên Backup Vault mà bạn đã tạo ở bước trước đó (Tên backup vault có phân biệt chữ hoa và chữ thường)
  - *--sns-topic-arn* : Nhập ARN của SNS topic chúng ta đã tạo trước đó. 

![Notification](../../../images/3/6.png?width=90pc)

3. Sau khi sửa lại câu lệnh cho phù hợp, hãy chạy lệnh trên để kích hoạt việc gửi thông điệp đến SNS Topic mỗi khi tiến trình Backup/Restore thành công.
4. Để kiểm tra lại việc thiết lập,  bạn có thể chạy lệnh ```aws backup get-backup-vault-notifications``` để kiểm tra thiết lập với SNS Topic ARN đã được cấu hình. Hãy nhớ thay đổi các thông số để phù hợp với hệ thống của bạn.

```bash
aws backup get-backup-vault-notifications --backup-vault-name sharenote-backup-vault --region ap-northeast-1
```

![Notification](../../../images/3/7.png?width=90pc)

Đến đây, bạn đã hoành thành việc kích hoạt nhận thông báo cho các hoạt động Backup/Restore thành công từ AWS Backup. Tiếp theo, chúng ta sẽ tiến hành kiểm tra hoạt động của AWS Backup.
