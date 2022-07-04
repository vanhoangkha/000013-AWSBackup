---
title : "Thiết lập thông báo"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Thiết lập thông báo

Trong đám mây, bạn có thể dễ dàng thiết lập thông báo để biết các sự kiện trong khối lượng công việc của mình. AWS Backup tận dụng AWS SNS để gửi các thông báo liên quan đến các hoạt động sao lưu đang diễn ra. Điều này sẽ cho phép hiển thị các trạng thái công việc dự phòng, khôi phục trạng thái công việc hoặc bất kỳ lỗi nào có thể đã xảy ra, cho phép các nhóm Vận hành của bạn phản hồi một cách thích hợp.

1. Mở Terminal có quyền truy cập vào AWS CLI. Đảm bảo rằng CLI được cập nhật và bạn có Quyền của quản trị viên AWS để chạy các lệnh AWS CLI.

   - Chỉnh sửa lệnh AWS CLI sau và bao gồm ARN của SNS TOPIC mà bạn đã tạo. Thay thế bằng ARN của SNS TOPIC thu được từ phần đầu ra của CloudFormation Stack.
```
aws backup put-backup-vault-notifications --region ap-southeast-1 --backup-vault-name BACKUP-LAB-VAULT --backup-vault-events BACKUP_JOB_COMPLETED RESTORE_JOB_COMPLETED --sns-topic-arn <YOUR SNS TOPIC ARN>
```
   - Sau khi chỉnh sửa, hãy chạy lệnh trên, nó sẽ bật thông báo với các thông báo được xuất bản lên SNS TOPIC mỗi khi hoàn thành công việc sao lưu hoặc khôi phục. Điều này sẽ đảm bảo Nhóm vận hành biết về bất kỳ lỗi nào khi sao lưu hoặc khôi phục dữ liệu.

![AWS Backup](/images/4/0001.png?featherlight=false&width=90pc)

2. Kiểm tra lại giao diện **SNS**

![AWS Backup](/images/4/0002.png?featherlight=false&width=90pc)

3. Bạn có thể xác minh rằng thông báo đã được bật bằng cách chạy lệnh sau. Đầu ra sẽ bao gồm một phần được gọi là SNSTopicArn, theo sau là ARN của SNS Topic đã được tạo.

```
aws backup get-backup-vault-notifications --backup-vault-name BACKUP-LAB-VAULT --region ap-southeast-1
```

![AWS Backup](/images/4/0003.png?featherlight=false&width=90pc)

Giờ đây, bạn đã kích hoạt thành công thông báo cho BACKUP-LAB-VAULT, đảm bảo rằng nhóm Vận hành biết về việc hoàn thành các hoạt động sao lưu và khôi phục liên quan đến vault này cũng như bất kỳ lỗi nào liên quan đến các hoạt động đó.
