+++
title = "Khởi tạo SNS Topic"
date = 2020
weight = 3
chapter = false
pre = "<b>3.1. </b>"
+++

Đầu tiên, chúng ta sẽ phải tạo SNS Topic để nhận các thông điệp từ AWS Backup để đưa đến các Subcriber mà chúng ta thiết lập.

{{% notice info %}}
Mục tiêu trong bài thực hành này, bạn sẽ thiết lập để nhận các thông báo liên quan đến AWS Backup được gửi đến email của bạn về các hành động Backup/Restore thành công.
{{% /notice %}}

**Nội dung:**
- [Tạo SNS Topic](#tạo-sns-topic)
- [Tạo SNS Subcription](#tạo-sns-subcription)

#### Tạo SNS Topic

1. Truy cập vào **AWS Management Console**, tìm **Amazon SNS** trong menu **Services** để truy cập vào Amazon SNS console.
2. Ở thanh điều hướng, chọn **Topics**.
3. Chọn **Create topic** để tạo SNS Topic mới.
![SNS](../../../images/3/1.png?width=60pc)
4. Trong trang **Create topic**, thiết lập các thông số cho SNS Topic:
   - Type: Chọn loại queue mà bạn muốn sử dụng (VD: **Standard**)
   - Name: Nhập tên topic (VD: **sharenote-backup-sns**)
5. Chọn **Create topic**.
6. Sau khi tạo thành công, thông tin SNS Topic vừa tạo sẽ được hiện ra.
![SNS](../../../images/3/2.png?width=60pc)
7. Hãy ghi chú lại ARN của SNS Topic để sử dụng ở bước tiếp theo của bài thực hành. (VD: **arn:aws:sns:ap-northeast-1:340879421878:sharenote-backup-sns**)

#### Tạo SNS Subcription

Để tạo subcriber nhận các thông báo từ AWS Backup, chúng ta sẽ tiến hành tạo như sau:

1. Từ trang thông tin SNS Topic, trong mục **Subscriptions**, chọn **Create subscription**.
![SNS](../../../images/3/3.png?width=60pc)
2. Trong trang Create subscription, thiết lập các thông tin cho Subcriber:
   - Topic ARN: Chọn SNS Topic vừa tạo ở bước trước (VD: **arn:aws:sns:ap-northeast-1:340879421878:sharenote-backup-sns**)
   - Protocol: Lựa chọn phương thức nhận thông báo (Trong bài thực hành, chúng ta sẽ sử dụng **Email**)
   - Endpoint (Xuất hiện sau khi lựa chọn Protocol): Nhập thông tin của Subcriber (VD: **subcriber@example.com**)
![SNS](../../../images/3/4.png?width=60pc)
3. Chọn **Create subscription**.
4. Sau khi tạo xong Subcription, hãy vào kiểm tra email đã đăng kí và chọn vào liên kết trong email nhận được từ SNS để tiến hành xác nhận đăng kí nhận thông báo.
![SNS](../../../images/3/5.png?width=30pc)