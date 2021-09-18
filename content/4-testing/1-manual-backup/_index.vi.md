+++
title = "Tạo bản Sao lưu"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++
#### Tổng quan

Ở bước này, bạn sẽ tiến hành tạo Sao lưu cho EBS Volume của mà ShareNote Instance đang sử dụng.

**Nội dung:**
- [Tạo bản Sao lưu cho EBS Volume](#tạo-bản-sao-lưu-cho-ebs-volume)

#### Tạo bản Sao lưu cho EBS Volume

Để tạo một bảo sao lưu, bạn sẽ sử dụng chức năng Create On-demand Backup của AWS Backup.

1. Truy cập vào **AWS Backup Console**.
2. Chọn **Dashboard** ở thanh bên trái và chọn **Protected resources** sau đó click chọn **Create an on demand backup**.

3. Trong trang **Create an on-demand Backup**, thiết lập các thông số cho bản sao lưu:
    - **Resource Type**: EBS
    - **Volume ID**: chọn Volume của ShareNote Instance đang chạy ứng dụng của bạn.
    - **Backup window**: Lựa chọn thời gian để khởi chạy tiến trình sao lưu. (VD: **Create backup now**)
    - **Retention period**: Chọn **Days** với giá trị **1**. (Với mục tiêu thực hành, bạn sẽ để thời gian hiệu lực của bản sao lưu này là 1 ngày)
    - **Backup vault**: chọn Backup Vault đã tạo trước đó cho ứng dụng ShareNote (VD: **sharenote-backup-vault**)
4. Chọn **Create on-demand backup**.
    ![4.1_CreateOnDemandBackup](../../../images/4/4.1_CreateOnDemandBackupPrompt.png?width=90pc)

5. Trong danh sách **Backup jobs** sẽ hiện ra tiến trình Backup ở trạng thái **Created** sau đó sẽ chuyển sang **Running**.

6. Sẽ mất 5 - 15 phút để tiến trình này hoàn thành và bạn sẽ thấy trạng thái thay đổi từ **Running** sang **Completed**.

Vậy là bạn đã hoàn thành việc tạo một bản sao lưu cho EBS Volume. 

{{% notice tip %}}
Ngoài ra, bạn cũngcó thể thử tạo thêm một bản sao lưu cho RDS Database mà bạn đang sử dụng cho ứng dụng ShareNote.
{{% /notice %}}
