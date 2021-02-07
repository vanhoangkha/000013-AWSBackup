+++
title = "Create a Backup"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++

Ở bước cuối cùng này, chúng ta sẽ tiến hành kiểm tra các hoạt động của AWS Backup bằng việc thực hiện Sao lưu, Khôi phục cũng như xem các thông báo được gửi đến sau khi tiến trình được hoàn tất.

**Contents:**
- [Create a Backup for EBS Volume](#create-a-backup-for-ebs-volume)

#### Create a Backup for EBS Volume

Để tạo một bảo sao lưu, chúng ta sẽ sử dụng chức năng Create On-demand Backup của AWS Backup.

1. Truy cập vào **AWS Backup Console**.
2. Ở Dashboard, chọn **Create an on-demand Backup**.

![Backup](../../../images/4/1.png?width=90pc)

3. Trong trang **Create an on-demand Backup**, thiết lập các thông số cho bản sao lưu:
   - Resource: Chọn resource mà bạn muốn sao lưu.
     - Resource Type: **EBS**
     - Volume ID: **vol-05114cb10f3122689** (Volume của ShareNote Instance đang chạy ứng dụng của chúng ta)
   - Backup window: Lựa chọn thời gian để khởi chạy tiến trình sao lưu. (VD: **Create backup now**)
   - Expire: Chọn **Days after creation** với giá trị **1**. (Với mục tiêu thực hành, chúng ta sẽ để thời gian hiệu lực của bản sao lưu này là 1 ngày)
   - Backup vault: Chúng ta sẽ chọn Backup Vault đã tạo trước đó cho ứng dụng ShareNote (VD: **sharenote-backup-vault**)

![Backup](../../../images/4/2.png?width=90pc)

4. Chọn **Create on-demand backup**.
5. Trong danh sách **Backup jobs** sẽ hiện ra tiến trình Backup ở trạng thái **Created** sau đó sẽ chuyển sang **Running**.

![Backup](../../../images/4/3.png?width=90pc)

![Backup](../../../images/4/4.png?width=90pc)

6. Sẽ mất 5 - 15 phút để tiến trình này hoàn thành và bạn sẽ thấy trạng thái thay đổi từ **Running** sang **Completed**.

![Backup](../../../images/4/5.png?width=90pc)

![Backup](../../../images/4/6.png?width=90pc)

Vậy là chúng ta đã hoàn thành việc tạo một bản sao lưu cho EBS Volume. 

{{% notice tip %}}
Ngoài ra, bạn có thể thử tạo thêm một bản sao lưu cho RDS Database mà chúng ta đang sử dụng cho ứng dụng ShareNote.
{{% /notice %}}
