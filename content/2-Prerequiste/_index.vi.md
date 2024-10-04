---
title: "Các bước chuẩn bị"
date: "2023-05-24"
weight: 2
chapter: false
pre: "<b>2. </b>"
---

#### Chuẩn bị trước

Trong phần này, chúng ta sẽ sử dụng **CloudFormation** (Dịch vụ quản lý cấu hình đám mây) để tạo các tài nguyên cần thiết cho bài lab. **CloudFormation stack** (Tổ hợp CloudFormation) sẽ tự động tạo ra các dịch vụ như **EC2 instance** (Máy chủ ảo EC2), **SNS Topic** (Chủ đề SNS), và **Lambda Function** (Hàm Lambda).

#### Nội dung

1. [Tạo S3 bucket](2.1-creates3bucket/)
2. [Triển khai cơ sở hạ tầng](2.2-deployinfras/)