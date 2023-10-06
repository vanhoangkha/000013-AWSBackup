---
title : "Triển khai hạ tầng"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

#### Triển khai hạ tầng

Trong bài thực hành này, bạn sẽ làm quen với việc sử dụng **AWS Backup** để tạo ra một kế hoạch sao lưu (backup plan) cho các tài nguyên đang hoạt động trên AWS như EBS Volumes, RDS Databases, DynamoDB Tables, hay EFS File Systems. Đồng thời, bạn cũng sẽ biết được làm thế nào để khôi phục lại dữ liệu từ các bản sao lưu và tự động hóa toàn bộ quá trình.

Đối với nhiều tổ chức, dữ liệu mà họ sở hữu là một trong những tài sản quý giá nhất mà họ có. Sao lưu dữ liệu thường xuyên có tầm quan trọng sống còn đối với sự thành công lâu dài của bất kỳ tổ chức nào. Tuy nhiên, một bản sao lưu dữ liệu chỉ có giá trị nếu dữ liệu có thể được khôi phục / khôi phục từ bản sao lưu. Trong đám mây, việc sao lưu dữ liệu và kiểm tra khôi phục dễ dàng hơn so với các trung tâm dữ liệu tại chỗ. Tự động hóa quy trình này với các hệ thống thông báo thích hợp sẽ đảm bảo rằng dữ liệu của tổ chức được sao lưu thường xuyên, các bản sao lưu được kiểm tra để đảm bảo khôi phục dự kiến ​​và những người thích hợp được thông báo trong trường hợp có lỗi.

![AWS Backup](/images/0/architecture.jpeg?featherlight=false&width=60pc)

1. Truy cập giao diện **AWS Management Console**

   - Tìm và chọn **CloudFormation**

![AWS Backup](/images/2-preparation/22.png?featherlight=false&width=90pc)

2. Chọn **Create stack**

![AWS Backup](/images/2-preparation/23.png?featherlight=false&width=90pc)

3. Trong giao diện **Create stack**

   - Đối với **PREREQUISITE - PREPARE TEMPLATE**, Chọn **Template is ready**
   - Đối với **SPECIFY TEMPLATE**, Chọn **Amazon S3 URL**
   - Đối với **Amazon S3 URL**, nhập URL bạn đã tạo.
   - Chọn **Next**

![AWS Backup](/images/2-preparation/24.png?featherlight=false&width=90pc)

4. Trong phần **STACK NAME**, nhập **Buckup-plan** (nhập tùy ý bạn)

   - Chọn **AvailabilityZone**
   - Đối với **LatestAmiId**, chọn giá trị mặc định.
   - Đối với **NotificationEmail**, nhập email của bạn để nhận thông báo.
   - Đối với **S3BucketName**, nhập tên **S3 bucket** bạn đã tạo.
   - Đối với **S3KeyLambdaZip**, nhập đường dẫn của **lambda_function.zip**

![AWS Backup](/images/2-preparation/25.png?featherlight=false&width=90pc)

5. Trong phần **CONFIGURE STACK OPTIONS**, Chọn **Next**

![AWS Backup](/images/2-preparation/26.png?featherlight=false&width=90pc)

6. Đối với **CAPABILITIES**, Chọn **I acknowledge that AWS CloudFormation might create IAM resources.**

   - Chọn **Submit**

![AWS Backup](/images/2-preparation/27.png?featherlight=false&width=90pc)

7. Hoàn thành tạo stack Cloudformation

![AWS Backup](/images/2-preparation/28.png?featherlight=false&width=90pc)

8. Kiểm tra lại **Output** của stack CloudFormation

![AWS Backup](/images/2-preparation/29.png?featherlight=false&width=90pc)

9. Chọn vào **Value** của **ApplicationURL**

![AWS Backup](/images/2-preparation/30.png?featherlight=false&width=90pc)

10. Kiểm tra mail sẽ nhận được mail thông báo.

![AWS Backup](/images/2-preparation/31.png?featherlight=false&width=90pc)

11. Thực hiện xác nhận mail.

![AWS Backup](/images/2-preparation/32.png?featherlight=false&width=90pc)
