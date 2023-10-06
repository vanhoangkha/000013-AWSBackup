---
title : "Tạo S3 Bucket"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

#### Tạo S3 Bucket

Trong phần này, chúng ta sẽ sử dụng **CloudFormation** để tạo resource cho bài lab. **CloudFormation** stack sẽ tạo các tài nguyên dịch vụ như **EC2 instance**, **SNS Topic** và **Lambda Function**

## Bước 1: Tải Template và Lambda Function

Tải [template CloudFormation và Lambda Function](https://github.com/AWS-First-Cloud-Journey/Backup-Plan/archive/refs/heads/master.zip).

1. Sau khi tải **template CloudFormation và Lambda Function** từ link trên:

   - Chúng ta sẽ tạo một **S3 bucket** để lưu trữ source.
   - Truy cập vào **AWS Management Console**, tìm và chọn **S3**.

![AWS Backup](/images/2-preparation/1.png?featherlight=false&width=90pc)

2. Trong giao diện **S3**, chọn **Create bucket**.

![AWS Backup](/images/2-preparation/2.png?featherlight=false&width=90pc)

3. Trong giao diện **Create bucket**:

   - Nhập **Bucket name**, phải nhập tên duy nhất, bạn có thể chọn tùy ý (Nếu trùng sẽ dẫn đến lỗi và không khởi tạo bucket được).

![AWS Backup](/images/2-preparation/3.png?featherlight=false&width=90pc)

::: tip Lưu ý
Trong workshop này, chúng ta sẽ sử dụng Region Singapore (ap-southeast-1). Nếu bạn muốn sử dụng Region khác, hãy đảm bảo chuyển Region về Region bạn muốn sử dụng khi tạo các tài nguyên liên quan tới workshop.
:::

4. Giữ nguyên cấu hình.

![AWS Backup](/images/2-preparation/4.png?featherlight=false&width=90pc)

5. Tại mục **Default encryption**, chọn **Disable**, sau đó chọn **Create bucket**.

![AWS Backup](/images/2-preparation/5.png?featherlight=false&width=90pc)

6. Hoàn thành tạo **S3 bucket**.

![AWS Backup](/images/2-preparation/6.png?featherlight=false&width=90pc)

7. Thực hiện tạo một folder lưu trữ.

![AWS Backup](/images/2-preparation/7.png?featherlight=false&width=90pc)

8. Trong giao diện tạo một folder:

   - Nhập tên **Folder name**.
   - Chọn **Create folder**.

![AWS Backup](/images/2-preparation/8.png?featherlight=false&width=90pc)

9. Hoàn thành tạo một folder.

![AWS Backup](/images/2-preparation/9.png?featherlight=false&width=90pc)

10. Trong folder vừa tạo, thực hiện **Upload** các file đã tải về và đã giải nén.

![AWS Backup](/images/2-preparation/10.png?featherlight=false&width=90pc)

11. Trong phần **Upload**:

    - Chọn **Add files**.
    - Chọn các file muốn tải lên.
    - Chọn **Upload**.

![AWS Backup](/images/2-preparation/11.png?featherlight=false&width=90pc)

12. Hoàn thành tải các file.

![AWS Backup](/images/2-preparation/12.png?featherlight=false&width=90pc)

13. Thực hiện cấu hình **Permissions** cho **S3 bucket**:

    - Đối với **Block public access (bucket settings)**.

![AWS Backup](/images/2-preparation/13.png?featherlight=false&width=90pc)

14. Bỏ chọn **Block all public access**:

    - Sau đó, chọn **Save changes**.

![AWS Backup](/images/2-preparation/14.png?featherlight=false&width=90pc)

15. Xác nhận bằng cách chọn **confirm** và sau đó chọn **Confirm**.

![AWS Backup](/images/2-preparation/15.png?featherlight=false&width=90pc)

16. Sau đó sẽ thực hiện cấu hình **Bucket policy**:

    - Chọn **Edit**.

![AWS Backup](/images/2-preparation/16.png?featherlight=false&width=90pc)

17. Trong giao diện **Edit bucket policy**:

    - Nhập đoạn code sau và thay bằng **Bucket ARN** của bạn.

    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "PublicReadGetObject",
                "Effect": "Allow",
                "Principal": "*",
                "Action": [
                    "s3:GetObject"
                ],
                "Resource": [
                    "arn:aws:s3:::Bucket-Name/*"
                ]
            }
        ]
    }
    ```

![AWS Backup](/images/2-preparation/17.png?featherlight=false&width=90pc)

18. Chọn **Save changes**.

![AWS Backup](/images/2-preparation/18.png?featherlight=false&width=90pc)

19. Kiểm tra **Permissions** đã **Public**.

![AWS Backup](/images/2-preparation/19.png?featherlight=false&width=90pc)

20. Sao chép thông tin đường dẫn của **lambda_function.zip**.

![AWS Backup](/images/2-preparation/20.png?featherlight=false&width=90pc)

21. Sao chép thông tin **Object URL** của file **backup-lab.yaml**.

![AWS Backup](/images/2-preparation/21.png?featherlight=false&width=90pc)
