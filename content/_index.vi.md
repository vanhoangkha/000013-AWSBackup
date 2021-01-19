+++
title = "Triển khai AWS Backup cho hệ thống"
date = 2020
weight = 1
chapter = false
+++

# Triển khai AWS Backup cho hệ thống

Trong bài thực hành này, chúng ta sẽ làm quen với việc tạo ra mội kế hoạch sao lưu cho các tài nguyên đang hoạt động trên AWS như EBS Volumes, RDS Databases, DynamoDB Tables, hay EFS File Systems. Đồng thời, chúng ta cũng sẽ biết được làm thế nào để khôi phục lại dữ liệu từ các bản sao lưu và tự động hóa toàn bộ quá trình.

Và trong bài thực hành này, chúng ta sẽ thử tạo nên một quy trình sao lưu cho ứng dụng ShareNote và tạo thử sao lưu cho EBS Volume của máy chủ chạy ứng dụng này với AWS Backup. Đông thời cũng sẽ tự động hóa quá trình này bằng việc tạo ra Backup Plan và thử nghiệm việc nhận các thông báo khi các tiến trình của AWS Backup chạy hoàn tất.

#### Mục tiêu

- Tạo được Backup Plan cho hệ thống để tự động hóa việc sao lưu.
- Kiểm thử hoạt động sao lưu/ phục hồi.
- Kiểm thử thông báo khi các tiến trình hoàn tất.