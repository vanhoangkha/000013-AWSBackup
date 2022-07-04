---
title : "Tạo S3 Bucket"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

#### Tạo S3 Bucket

Trong phần này, chúng ta sẽ sử dụng **CloudFormation** để tạo resource cho bài lab. **CloudFormation** stack sẽ tạo các tài nguyên dịch vụ như **EC2 instance**, **SNS Topic** và **Lambda Function**

Bước đầu tiên chúng ta cần phải tải [template CloudFormation và Lambda Function](https://github.com/AWS-First-Cloud-Journey/Backup-Plan/archive/refs/heads/master.zip)

1. Sau khi tải **[template CloudFormation và Lambda Function](https://github.com/AWS-First-Cloud-Journey/Backup-Plan/archive/refs/heads/master.zip)**

   - Chúng ta sẽ tạo một **S3 bucket** để lưu trữ source.
   - Truy cập vào **AWS Management Console**, tìm và chọn **S3**


![AWS Backup](/images/1/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **S3**, chọn **Create bucket**

![AWS Backup](/images/1/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create bucket**

   - Nhập **Bucket name**, phải nhập tên duy nhất, bạn có thể chọn tùy ý (Nếu trùng sẽ dẫn đến lỗi và không khởi tạo bucket được)

![AWS Backup](/images/1/0003.png?featherlight=false&width=90pc)

4. Giữ nguyên cấu hình.

![AWS Backup](/images/1/0004.png?featherlight=false&width=90pc)

5. Chọn **Create bucket**

![AWS Backup](/images/1/0005.png?featherlight=false&width=90pc)

6. Hoàn thành tạo **S3 bucket**

![AWS Backup](/images/1/0006.png?featherlight=false&width=90pc)

7. Thực hiện tạo một folder lưu trữ  

![AWS Backup](/images/1/0007.png?featherlight=false&width=90pc)

8. Trong giao diện tạo một folder 


   - Nhập tên **Folder name**
   - Chọn **Create folder**

![AWS Backup](/images/1/0008.png?featherlight=false&width=90pc)

9. Hoàn thành tạo một folder

![AWS Backup](/images/1/0009.png?featherlight=false&width=90pc)

10. Trong folder vừa tạo, thực hiện **Upload** các file đã tải về và đã giải nén.

![AWS Backup](/images/1/00010.png?featherlight=false&width=90pc)

11. Trong phần **Upload**

    - Chọn **Add files**
    - Chọn các file muốn tải lên.
    - Chọn **Upload**

![AWS Backup](/images/1/00011.png?featherlight=false&width=90pc)

12. Hoàn thành tải các file 

![AWS Backup](/images/1/00012.png?featherlight=false&width=90pc)

13. Thực hiện cấu hính **Permissions** cho **S3 bucket**

    - Đối với **Block public access (bucket settings)**

![AWS Backup](/images/1/00013.png?featherlight=false&width=90pc)

14. Bỏ chọn ***Block all public access**

    - Sau đó, chọn **Save changes**

![AWS Backup](/images/1/00014.png?featherlight=false&width=90pc)

15. Xác nhận bằng **confirm**và chọn **Confirm**

![AWS Backup](/images/1/00015.png?featherlight=false&width=90pc)

16. Sau đó sẽ thực hiện cấu hình **Bucket policy**

    - Chọn **Edit**

![AWS Backup](/images/1/00016.png?featherlight=false&width=90pc)

17. Trong giao diện **Edit bucket policy**

    - Nhập đoạn code  sau và thay bằng **Bucket ARN** của bạn.


```
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

![AWS Backup](/images/1/00017.png?featherlight=false&width=90pc)

18. Chọn **Save changes**

![AWS Backup](/images/1/00018.png?featherlight=false&width=90pc)

19. Kiểm tra **Permissions** đã **Public**

![AWS Backup](/images/1/00019.png?featherlight=false&width=90pc)

20. Sao chép thông tin đường dẫn của **lambda_function.zip**

![AWS Backup](/images/1/00020.png?featherlight=false&width=90pc)

21. Sao chép thông tin **Object URL** của file **backup-lab.yaml**

![AWS Backup](/images/1/00021.png?featherlight=false&width=90pc)