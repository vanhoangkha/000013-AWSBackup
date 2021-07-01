+++
title = "Triển khai AWS Backup cho hệ thống"
date = 2020
weight = 1
chapter = false
+++

# Triển khai AWS Backup cho hệ thống

#### Tổng quan

Trong bài thực hành này, bạn sẽ làm quen với việc sử dụng **AWS Backup** để tạo ra một kế hoạch sao lưu (*backup plan*) cho các tài nguyên đang hoạt động trên AWS như EBS Volumes, RDS Databases, DynamoDB Tables, hay EFS File Systems. Đồng thời, bạn cũng sẽ biết được làm thế nào để khôi phục lại dữ liệu từ các bản sao lưu và tự động hóa toàn bộ quá trình.

Cụ thể, bạn sẽ thử tạo nên một quy trình sao lưu cho ứng dụng ShareNote và tạo thử sao lưu cho EBS Volume của máy chủ chạy ứng dụng này với AWS Backup. Đồng thời, bạn cũng sẽ tự động hóa quá trình này bằng việc tạo ra Backup Plan và thử nghiệm việc nhận các thông báo khi các tiến trình của AWS Backup chạy hoàn tất.

#### Mục tiêu

- Tạo được Backup Plan cho hệ thống để tự động hóa việc sao lưu.
- Kiểm thử hoạt động sao lưu/ phục hồi.
- Kiểm thử thông báo khi các tiến trình hoàn tất.

#### AWS Backup
**AWS Backup** là một dịch vụ bảo vệ dữ liệu (*data protection*) được AWS quản lý cho phép bạn tập trung và tự động hóa quy trình bảo vệ dữ liệu cho các tài nguyên AWS trên cloud và on-prem. Với AWS Backup, bạn có thể thiết lập và tự động hóa các chính sách sao lưu và kế hoạch sao lưu của bạn từ một nơi duy nhất. 

#### AWS Simple Notification Service (SNS)
**AWS SNS** là dịch vụ cho phép bạn gửi thông báo từ nhà xuất bản (*publisher*) tới đối tượng đăng ký (*subscriber*). Publisher giao tiếp không đồng bộ với subscriber thông qua một chủ đề (*topic*). Có nghĩa là, Publisher sẽ gửi thông báo tới topic, sau đó topic ấy sẽ gửi thông báo ấy tới các subscriber đang đăng ký theo dõi topic đó.

#### Nội dung:
1. [Chuẩn bị Hạ tầng](1-deploy-infrastructure)
2. [Khởi tạo Backup Plan](2-create-backup-plan)
3. [Thiết lập Notification](3-notifications)
4. [Kiểm tra hoạt động](4-testing)