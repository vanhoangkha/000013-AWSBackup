+++
title = "Khởi tạo Backup Plan"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

**Nội dung:**
- [1. Khởi tạo Backup Plan](#1-khởi-tạo-backup-plan)
- [2. Thiết lập các Resource sẽ sử dụng Backup Plan](#2-thiết-lập-các-resource-sẽ-sử-dụng-backup-plan)

#### 1. Khởi tạo Backup Plan

Để thiết lập AWS Backup cho toàn bộ hệ thống của bạn trước hết chúng ta sẽ tiến hành tạo Backup Plan.

1. Truy cập vào **AWS Management Console**, tìm **AWS Backup** trong menu **Services** để truy cập vào AWS Backup console.
2. Ở thanh điều hướng, chọn **Backup plans**.
3. Chọn **Create Backup plan** để tạo mới.

![Backup Plan](../../../images/2/1.png?width=60pc)

4. Ở trang **Create Backup plan**, lựa chọn các thiết lập như sau:
   - Choose how you want to begin: chọn **Build a new plan**
   - Backup plan name: Nhập tên muốn đặt (VD: **sharenote-backup**)
   - Rule name: Nhập tên rule muốn đặt (VD: **sharenote-backup-rule**)
   - Schedule: 
     - Frequency: Lựa chọn thiết lập tùy theo nhu cầu của bạn về RPO của bạn
     - Backup window: Lựa chọn khung thời gian tiến hành backup. (Bạn cần cân nhắc về khoảng thời gian này vì một số resource khi tiến hành sao lưu sẽ bị ảnh hưởng đến khả năng hoạt động trong khoảng thời gian sao lưu). Đối với bài thực hành này, chúng ta sẽ chọn **Use backup window defaults - recommended**.
![Backup Plan](../../../images/2/2.png?width=60pc)
     - Lifecycle (tùy chọn): Thiết lập này cho phép bạn có thể di chuyển các bản sao lưu vào cold storage hoặc thiết lập thời gian hiệu lực để tiết kiệm chi phí. Thiết lập này hiện tại **chỉ hỗ trợ cho các sao lưu của EFS**. Trong bài thực hành này, chúng ta sẽ chọn **Never** cho cả **Transition to cold storage** và **Expire**.
![Backup Plan](../../../images/2/3.png?width=60pc)
   - Backup Vault: Chọn **Create new Backup Vault**, cửa sổ **Create Backup vault** sẽ xuất hiện.
     - Backup vault name: Nhập tên của Backup Vault (VD: **sharenote-backup-vault**)
     - Master key: Chọn KMS key bạn đã tạo. Trong bài thực hành này, chúng ta sẽ chọn **(default) aws/backup**.
     - Chọn **Create Backup Vault**.

{{% notice tip %}}
Bạn nên sử dụng các Backup Vault khác nhau cho các hạ tầng khác nhau.
{{% /notice %}}

![Backup Plan](../../../images/2/4.png?width=60pc)

   - Generate copy - *optional*: Bạn có thể lựa chọn thêm việc nhân bản bản sao lưu của bạn sang một Region khác để tăng khả năng dự phòng. Trong khuôn khổ bài thực hành, chúng ta sẽ không thiết lập tính năng này.
   - Tags added to Backup plan: Bạn có thể thêm các đánh dấu cho Backup plan của mình.

![Backup Plan](../../../images/2/5.png?width=60pc)

#### 2. Thiết lập các Resource sẽ sử dụng Backup Plan

Việc gán các Resource sử dụng Backup Plan là bước xác định bạn sẽ tiến hành tạo các sao lưu cho Resource nào cần thiết cho hệ thống của bạn.
Chúng ta sẽ tiến hành gán các resource với Backup Plan như sau:

1. Truy cập vào **AWS Management Console**, tìm **AWS Backup** trong menu **Services** để truy cập vào AWS Backup console.
2. Ở thanh điều hướng, chọn **Backup plans**.
3. Chọn backup plan đã tạo ở trên (sharenote-backup) để vào trang thông tin chi tiết của backup plan.
4. Ở mục **Resource assignments**, chọn **Assign resources**.

![Backup Plan](../../../images/2/6.png?width=60pc)

5. Trong trang **Assign resources**, bạn cần nhập các thông tin để xác định các resource sẽ được gán vào backup plan.
   - Ở mục **General**:
     - Resource assignment name: Đặt tên cho nhóm resource mà bạn gán. (VD: **sharenote-backup-resources**)
     - IAM role: Chọn **Default role**
   - Ở mục **Assign resource**:
     - Assign by: Chọn **Tags**.
     - Key: Nhập giá trị Key (VD: **workload**)
     - Value: Nhập giá trị Value (VD: **ShareNoteApp**)

{{% notice info %}}
Trong trường hợp sử dụng **Tags** để gom nhóm các resource, hãy đảm bảo rằng các resource đều được đánh dấu với Tag tương ứng.
{{% /notice %}}

![Backup Plan](../../../images/2/7.png?width=60pc)

{{% notice info %}}
Trong trường hợp bạn muốn sử dụng các **Resource ID** để xác định từng resource theo từng **Resource type**.
{{% /notice %}}

![Backup Plan](../../../images/2/8.png?width=60pc)
6. Cuối cùng, chọn **Assign resources**.