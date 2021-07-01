+++
title = "Khởi tạo SNS Topic"
date = 2020
weight = 3
chapter = false
pre = "<b>3.1. </b>"
+++

#### Tổng quan

Bạn sẽ phải tạo SNS Topic để nhận các thông báo từ AWS Backup đến các Subcriber mà bạn thiết lập.

**Nội dung:**
- [Tạo SNS Topic](#tạo-sns-topic)
- [Tạo SNS Subcription](#tạo-sns-subcription)

#### Tạo SNS Topic

1. Truy cập vào **AWS Management Console**, tìm **Amazon SNS** trong menu **Services** để truy cập vào **Amazon SNS console**.
2. Ở thanh điều hướng, chọn **Topics**.
3. Chọn **Create topic** để tạo SNS Topic mới.
![3_CreateTopic](../../../images/3/3_CreateTopic.png?width=90pc)

4. Trong trang **Create topic**, thiết lập các thông số cho SNS Topic như sau:
   - **Type**: Chọn loại queue mà bạn muốn sử dụng (VD: **Standard**). Có hai loại queue:
      - **FIFIO (first-in, first-out)**: thông báo sẽ được tiếp nhận và chuyển đi theo trật tự FIFO nghiêm khắc.
      - **Standard**: thông báo sẽ được tiếp nhận và chuyển đi với trật tự được nới lỏng. 
   - **Name**: Nhập tên topic (VD: **sharenote-backup-sns**)
5. Chọn **Create topic**.
6. Sau khi tạo thành công, thông tin SNS Topic vừa tạo sẽ được hiện ra.
7. Hãy ghi chú lại ARN của SNS Topic để sử dụng ở bước tiếp theo của bài thực hành.

![3_TopicARN](../../../images/3/3_TopicARN.png?width=90pc)

#### Tạo SNS Subcription

Để tạo subcriber nhận các thông báo từ AWS Backup, bạn sẽ tiến hành tạo như sau:

1. Từ trang thông tin của SNS Topic vừa được tạo, trong mục **Subscriptions**, chọn **Create subscription**.

![3_CreateSubscription](../../../images/3/3_CreateSubscription.png?width=90pc)

2. Trong trang Create subscription, thiết lập các thông tin cho Subcriber:
   - **Topic ARN**: Chọn SNS Topic vừa tạo ở bước trước
   - **Protocol**: Lựa chọn phương thức nhận thông báo (Trong bài thực hành, bạn sẽ sử dụng **Email**)
   - **Endpoint** (Xuất hiện sau khi lựa chọn Protocol): Nhập thông tin của Subcriber. Bạn có thể nhập email của chính bạn. (VD: **subcriber@example.com**)
3. Chọn **Create subscription**.
![3_CreateSubscriptionPrompt](../../../images/3/3_CreateSubscriptionPrompt.png?width=90pc)


4. Sau khi tạo xong Subcription, hãy vào kiểm tra email đã đăng kí và chọn vào liên kết trong email nhận được từ SNS để tiến hành xác nhận đăng kí nhận thông báo.
   ![SNS](../../../images/3/5.png?width=60pc)
