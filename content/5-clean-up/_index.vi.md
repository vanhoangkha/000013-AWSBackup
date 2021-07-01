+++
title = "Dọn dẹp tài nguyên"
date = 2021-06-18T14:25:30+07:00
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

1. Xóa SNS Subscriber
    - Truy cập vào AWS SNS Console
    - Chọn Subscription ở thanh bên trái
    - Chọn và xóa các Subscriber liên quan

2. Xóa SNS Topic
    - Truy cập vào AWS SNS Console
    - Chọn Topics ở thanh bên trái
    - Chọn và xóa Topic liên quan

3. Xóa Backup Vaults
    - Truy cập vào AWS Backup Console
    - Chọn Backup Vaults ở thanh bên trái
    - Chọn Backup Vault được tạo trong bài này
    - Ở mục Backups, tick vào backup đã tạo, chọn Actions, và chọn Delete
    - Ở trang thông tin Backup Vault, chọn Delete 

4. Xóa Backup Plans
    - Truy cập vào AWS Backup Console
    - Chọn Backup plans ở thanh bên trái
    - Chọn Backup plan được tạo trong bài này
    - Ở mục Resource assignments, chọn resource đã tạo và chọn Delete
    - Ở trang thông tin Backup plan, chọn Delete 

5. Xóa EBS Volume đã được khôi phục.
    - Truy cập vào AWS EC2 Console
    - Chọn Volumes ở thanh bên trái
    - Tick vào EBS Volume đã được khôi phục, chọn Actions, và chọn Delete Volume

5. Xóa hạ tầng của ứng dụng Sharenote. Bạn có thể tham khảo ở bài [TRIỂN KHAI ỨNG DỤNG SHARENOTE VỚI AUTO SCALING GROUP](https://000006.awsstudygroup.com/vi/)