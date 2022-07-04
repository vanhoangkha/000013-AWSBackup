---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Tổng quan

Trong bài thực hành này, bạn sẽ làm quen với việc sử dụng **AWS Backup** để tạo ra một kế hoạch sao lưu (backup plan) cho các tài nguyên đang hoạt động trên AWS như EBS Volumes, RDS Databases, DynamoDB Tables, hay EFS File Systems. Đồng thời, bạn cũng sẽ biết được làm thế nào để khôi phục lại dữ liệu từ các bản sao lưu và tự động hóa toàn bộ quá trình.

Đối với nhiều tổ chức, dữ liệu mà họ sở hữu là một trong những tài sản quý giá nhất mà họ có. Sao lưu dữ liệu thường xuyên có tầm quan trọng sống còn đối với sự thành công lâu dài của bất kỳ tổ chức nào. Tuy nhiên, một bản sao lưu dữ liệu chỉ có giá trị nếu dữ liệu có thể được khôi phục / khôi phục từ bản sao lưu. Trong đám mây, việc sao lưu dữ liệu và kiểm tra khôi phục dễ dàng hơn so với các trung tâm dữ liệu tại chỗ. Tự động hóa quy trình này với các hệ thống thông báo thích hợp sẽ đảm bảo rằng dữ liệu của tổ chức được sao lưu thường xuyên, các bản sao lưu được kiểm tra để đảm bảo khôi phục dự kiến ​​và những người thích hợp được thông báo trong trường hợp có lỗi.

![AWS Backup](/images/0/architecture.jpeg?featherlight=false&width=60pc)


#### Mục tiêu

- Tạo được Backup Plan cho hệ thống để tự động hóa việc sao lưu.
- Kiểm thử hoạt động sao lưu/ phục hồi.
- Kiểm thử thông báo khi các tiến trình hoàn tất.

#### AWS Backup

**AWS Backup** là một dịch vụ bảo vệ dữ liệu (data protection) được AWS quản lý cho phép bạn tập trung và tự động hóa quy trình bảo vệ dữ liệu cho các tài nguyên AWS trên cloud và on-prem. Với AWS Backup, bạn có thể thiết lập và tự động hóa các chính sách sao lưu và kế hoạch sao lưu của bạn từ một nơi duy nhất.

#### AWS Simple Notification Service (SNS)

**AWS SNS** là dịch vụ cho phép bạn gửi thông báo từ nhà xuất bản (publisher) tới đối tượng đăng ký (subscriber). Publisher giao tiếp không đồng bộ với subscriber thông qua một chủ đề (topic). Có nghĩa là, Publisher sẽ gửi thông báo tới topic, sau đó topic ấy sẽ gửi thông báo ấy tới các subscriber đang đăng ký theo dõi topic đó.

