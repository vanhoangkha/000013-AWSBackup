+++
title = "Restore from Backup"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++

Để khôi phục lại từ các bản sao lưu, chúng ta sẽ tiến hành chọn bản sao lưu đó và thực hiện khôi phục từ Backup vault như sau:

{{% notice info %}}
Hãy chắc chắn bạn đã thực hiện bước sao lưu ở phần trước để có một bản sao lưu sử dụng cho mục đích khôi phục.
{{% /notice %}}

**Contents:**
- [Restore EBS Volume from Backup](#restore-ebs-volume-from-backup)

#### Restore EBS Volume from Backup

1. Truy cập vào **AWS Backup Console**.
2. Chọn **Backup vaults**, chọn **sharenote-backup-vault** để xem danh sách các bản sao lưu.
![Backup](../../../images/4/8.png?width=60pc)
3. Trong mục **Backups**, chọn bản sao lưu mà bạn đã tạo ra trước đó (VD: **snapshot/snap-08c04048e4adf8721**).
![Backup](../../../images/4/9.png?width=60pc)
4. Chọn **Restore**.
5. Trong trang **Restore backup**, thiết lập các thông số liên quan đến EBS Volume mà chúng ta sẽ khôi phục lại.
   - Resource type:  **EBS volume**
   - Availability zone: Lựa chọn Availibility zone mà chúng ta sẽ lưu trữ Volume khôi phục này. (VD: **ap-northeast-1a**)
![Backup](../../../images/4/10.png?width=60pc)
6. Chọn **Restore backup**.
7. Danh sách **Restore jobs** sẽ hiển thị tiến trình khôi phục mà chúng ta vừa tạo ra ở trạng thái **Created** sau đó sẽ chuyển sang **Running**.
![Backup](../../../images/4/11.png?width=60pc)
8. Sẽ mất 5 - 15 phút để tiến trình này hoàn thành và bạn sẽ thấy trạng thái thay đổi từ **Running** sang **Completed**.
![Backup](../../../images/4/12.png?width=60pc)
![Backup](../../../images/4/14.png?width=60pc)