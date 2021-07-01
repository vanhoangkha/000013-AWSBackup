+++
title = "Thiết lập Notification"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

# cho AWS Backup với AWS SNS

#### Tổng quan

AWS Backup sử dụng AWS SNS để gửi các thông báo liên quan đến các hoạt động liên quan đến sao lưu được diễn ra trong hệ thống mà chúng ta đã thiết lập. Việc nhận các thông báo này cho chúng ta biết được thông tin về trạng thái các backup job đang chạy hoặc khi có các lỗi xảy ra nhằm cho phép chúng ta có những hành động kịp thời.

Ở phần này, chúng ta sẽ tiến hành kích hoạt tính năng gửi thông báo thông qua email khi những tiến trình của AWS Backup được thực thi hoàn tất. Để thiết lập thông báo, chúng ta sẽ sử dụng câu lệnh thông qua AWS CLI. (Bạn có thể tìm hiểu thêm về CLI thông qua [Sử dụng AWS CLI trên Windows/Ubuntu](https://000011.awsstudygroup.com/))

{{% notice tip %}}
Hãy chắc chắn bạn đã thiết lập AWS CLI trước khi thực hiện bài thực hành và chắc chắn chọn đúng Region mà bạn đang sử dụng.
{{% /notice %}}

#### Mục tiêu

Bạn sẽ thiết lập để nhận các thông báo của AWS Backup được gửi đến email của bạn về các hành động Backup/Restore thành công.

#### Nội dung:
- [3.1 Khởi tạo SNS Topic](1-create-sns-topic)
- [3.2 Thiết lập Notification](2-enable-notifications)