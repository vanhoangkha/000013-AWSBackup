+++
title = "Khôi phục từ bản Sao lưu"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++

#### Tổng quan

Để khôi phục lại từ các bản sao lưu, bạn sẽ tiến hành chọn bản sao lưu đó và thực hiện khôi phục từ Backup vault như sau:

{{% notice info %}}
Hãy chắc chắn bạn đã thực hiện bước sao lưu ở phần trước để có một bản sao lưu sử dụng cho mục đích khôi phục.
{{% /notice %}}

**Nội dung:**
- [Khôi phục EBS Volume từ bản sao lưu](#khôi-phục-ebs-volume-từ-bản-sao-lưu)

#### Khôi phục EBS Volume từ bản sao lưu

1. Truy cập vào **AWS Backup Console**.
2. Chọn **Backup vaults**, chọn **sharenote-backup-vault** để xem danh sách các bản sao lưu.
      ![4.2_BackupVaults](../../../images/4/4.2_BackupVaults.png?width=90pc)

3. Trong mục **Backups**, chọn bản sao lưu mà bạn đã tạo ra trước đó 

      ![4.2_RestoreBackup](../../../images/4/4.2_RestoreBackup.png?width=90pc)

4. Chọn **Actions** rồi chọn **Restore**.
5. Trong trang **Restore backup**, thiết lập các thông số liên quan đến EBS Volume mà bạn sẽ khôi phục lại.
   - **Resource type**:  EBS volume
   - **Availability zone**: Lựa chọn Availibility zone mà bạn sẽ lưu trữ Volume khôi phục này. (VD: **ap-southeast-1a**)
   - Các tùy chọn còn lại để mặc định
![4.2_RestoreBackupPrompt](../../../images/4/4.2_RestoreBackupPrompt.png?width=90pc)
6. Chọn **Restore backup**.
7. Danh sách **Restore jobs** sẽ hiển thị tiến trình khôi phục mà bạn vừa tạo ra ở trạng thái **Created** sau đó sẽ chuyển sang **Running**.

8. Sẽ mất 5 - 15 phút để tiến trình này hoàn thành và bạn sẽ thấy trạng thái thay đổi từ **Running** sang **Completed**.
9. Kiểm tra EBS Volume vừa mới được khôi phục lại.

![4.2_Success](../../../images/4/4.2_Success.png?width=90pc)
