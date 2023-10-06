---
title : "Thiết lập thông báo"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Thiết lập thông báo

Trong môi trường đám mây, bạn có thể dễ dàng thiết lập thông báo để biết về các sự kiện quan trọng trong lượng công việc của mình. AWS Backup sử dụng dịch vụ AWS SNS (Simple Notification Service) để gửi thông báo liên quan đến các hoạt động sao lưu đang diễn ra. Điều này cho phép bạn theo dõi trạng thái công việc sao lưu, khôi phục và các lỗi có thể xảy ra, giúp nhóm Vận hành phản ứng kịp thời và thích hợp.

#### Bước 1: Cấu hình AWS CLI

1. Mở Terminal và đảm bảo bạn có quyền truy cập vào AWS CLI. Hãy chắc chắn rằng phiên bản CLI đã được cập nhật và bạn có Quyền của quản trị viên AWS để thực thi các lệnh AWS CLI.

    > **Lưu ý:** Để thực hiện bước này, bạn cần cài đặt **AWS CLI** trên máy tính của bạn. Nếu bạn chưa cài đặt **AWS CLI**, bạn có thể tham khảo phần 1 và 2 của hướng dẫn [000011 - Sử dụng AWS CLI trên Windows/Ubuntu](https://000011.awsstudygroup.com/vi/).

2. Chỉnh sửa lệnh AWS CLI sau và thay thế bằng ARN của SNS TOPIC bạn đã tạo. ARN này có thể tìm thấy trong phần đầu ra của CloudFormation Stack.

    ```sh
    aws backup put-backup-vault-notifications --region ap-southeast-1 --backup-vault-name BACKUP-LAB-VAULT --backup-vault-events BACKUP_JOB_COMPLETED RESTORE_JOB_COMPLETED --sns-topic-arn <YOUR SNS TOPIC ARN>
    ```

3. Sau khi đã chỉnh sửa, thực thi lệnh trên. Điều này sẽ kích hoạt thông báo thông qua SNS TOPIC mỗi khi một công việc sao lưu hoặc khôi phục hoàn thành. Thông tin này giúp nhóm Vận hành nắm bắt được các lỗi có thể xảy ra trong quá trình sao lưu hoặc khôi phục dữ liệu.

   ![AWS Backup](/images/4-notification/1.png?featherlight=false&width=90pc)

#### Bước 2: Kiểm tra giao diện SNS

   ![AWS Backup](/images/4-notification/2.png?featherlight=false&width=90pc)

#### Bước 3: Xác minh thông báo

1. Để xác minh rằng thông báo đã được kích hoạt thành công, bạn có thể sử dụng lệnh sau. Kết quả đầu ra sẽ bao gồm một phần được gọi là SNSTopicArn, theo sau là ARN của SNS Topic đã được tạo.

    ```sh
    aws backup get-backup-vault-notifications --backup-vault-name BACKUP-LAB-VAULT --region ap-southeast-1
    ```

   ![AWS Backup](/images/4-notification/3.png?featherlight=false&width=90pc)

2. Bây giờ, bạn đã kích hoạt thành công thông báo cho BACKUP-LAB-VAULT, đảm bảo rằng nhóm Vận hành biết về việc hoàn thành các hoạt động sao lưu và khôi phục liên quan đến vault này cũng như bất kỳ lỗi nào liên quan đến các hoạt động đó.
