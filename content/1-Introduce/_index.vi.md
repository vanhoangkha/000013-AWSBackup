---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Tổng quan

Trong bài thực hành này, bạn sẽ làm quen với việc sử dụng **AWS Backup** để tạo ra một kế hoạch sao lưu (*backup plan*) cho các tài nguyên đang hoạt động trên AWS như EBS Volumes, RDS Databases, DynamoDB Tables, hay EFS File Systems. Đồng thời, bạn cũng sẽ biết được làm thế nào để khôi phục lại dữ liệu từ các bản sao lưu và tự động hóa toàn bộ quá trình.

Dành cho nhiều tổ chức, dữ liệu là một trong những tài sản quý giá nhất mà họ sở hữu. Sao lưu dữ liệu thường xuyên có tầm quan trọng sống còn đối với sự thành công lâu dài của bất kỳ tổ chức nào. Tuy nhiên, bản sao lưu dữ liệu chỉ có giá trị khi dữ liệu có thể được khôi phục từ nó. Trong môi trường đám mây, việc sao lưu và kiểm tra khôi phục dễ dàng hơn so với các trung tâm dữ liệu cục bộ. Tự động hóa quy trình này với hệ thống thông báo thích hợp đảm bảo rằng dữ liệu của tổ chức được sao lưu đều đặn, bản sao lưu được kiểm tra để đảm bảo khôi phục dự kiến, và những người liên quan được thông báo trong trường hợp có lỗi.

![AWS Backup](/images/0/architecture.jpeg?featherlight=false&width=60pc)

#### Mục tiêu

- Tạo kế hoạch sao lưu cho hệ thống để tự động hóa việc sao lưu.
- Thực hiện kiểm thử sao lưu/phục hồi.
- Thực hiện kiểm thử thông báo khi các quy trình hoàn tất.

#### AWS Backup

**AWS Backup** là một dịch vụ bảo vệ dữ liệu do AWS quản lý, cho phép bạn tập trung và tự động hóa quy trình bảo vệ dữ liệu cho các tài nguyên AWS trên môi trường đám mây và on-premises. Với AWS Backup, bạn có khả năng thiết lập và tự động hóa chính sách sao lưu cũng như kế hoạch sao lưu từ một nơi duy nhất.

#### AWS Simple Notification Service (SNS)

**AWS SNS** là dịch vụ cho phép bạn gửi thông báo từ bên gửi thông báo (publisher) tới các đối tượng đăng ký (subscriber). Bộ phát thông báo giao tiếp không đồng bộ với người nhận thông báo thông qua một chủ đề (topic). Điều này có nghĩa là, người gửi thông báo sẽ đưa thông báo vào chủ đề, sau đó chủ đề sẽ gửi thông báo đó đến các người nhận đăng ký theo dõi chủ đề tương ứng.
