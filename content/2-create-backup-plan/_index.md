+++
title = "Khởi tạo Backup Plan"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

#### Tổng quan

Ở phần này, bạn sẽ khởi tạo một kế hoạch sao lưu (*Backup Plan*) và gán các resource liên quan vào backup plan ấy.

**Nội dung:**
- [1. Khởi tạo Backup Plan](#1-khởi-tạo-backup-plan)
- [2. Thiết lập các Resource sẽ sử dụng Backup Plan](#2-thiết-lập-các-resource-sẽ-sử-dụng-backup-plan)

#### 1. Khởi tạo Backup Plan

Để thiết lập AWS Backup cho toàn bộ hệ thống của bạn trước hết chúng ta sẽ tiến hành tạo Backup Plan.

1. Truy cập vào **AWS Management Console**, tìm **AWS Backup** trong menu **Services** để truy cập vào **AWS Backup Console**.
2. Ở thanh điều hướng, chọn **Backup plans**.
3. Chọn **Create Backup plan** để tạo mới.

![Creat Backup Plan](../../../images/2/2_CreateBackupPlan.png?width=90pc)

4. Ở trang **Create Backup plan**, lựa chọn các thiết lập như sau:
    ![2_StartOptions](../../../images/2/2_StartOptions.png?width=90pc)
    - Mục **Start options**:  
      - **Choose how you want to begin**: chọn **Build a new plan** để tạo một backup plan hoàn toàn mới
      - **Backup plan name**: Nhập tên muốn đặt (VD: **sharenote-backup**)
    - Mục **Backup rule configuration**:
      - **Backup rule name**: Nhập tên rule muốn đặt (VD: **sharenote-backup-rule**)
      - **Backup Vault**: Chọn **Create new Backup Vault** và cửa sổ **Create Backup vault** sẽ xuất hiện.
        - **Backup vault name**: Nhập tên của Backup Vault (VD: **sharenote-backup-vault**)
        - **Master key**: Chọn KMS key bạn đã tạo. Trong bài thực hành này, chúng ta sẽ chọn **(default) aws/backup**.
        - Chọn **Create Backup Vault**.
        ![Backup Plan](../../../images/2/2_BackupVault.png?width=90pc)
{{% notice tip %}}
Bạn nên sử dụng các Backup Vault khác nhau cho các hạ tầng khác nhau.
{{% /notice %}}
      - **Backup frequency**: Lựa chọn thiết lập tùy theo nhu cầu của bạn về Recovery Point Objective (RPO) của bạn. (Ví dụ: Daily)
      - **Backup window**: Lựa chọn khung thời gian tiến hành backup. Đối với bài thực hành này, chúng ta sẽ chọn **Use backup window defaults - recommended**.
{{% notice note %}}
Bạn cần cân nhắc về khoảng thời gian này vì một số resource khi tiến hành sao lưu sẽ bị ảnh hưởng đến khả năng hoạt động trong khoảng thời gian sao lưu.
{{% /notice %}}
      - **Transition to cold storage**: Sau khoảng thời gian này, AWS Backup sẽ tự động chuyển các bản sao lưu các bạn thành dữ liệu **lạnh** (*cold storage*) để tiết kiệm chi phí. Trong bài thực hành này, bạn sẽ chọn **Never**
      - **Retention period**: bạn sẽ thiết lập khoảng thời gian tồn tại của các bản sao lưu. AWS Backup sẽ tự động xóa các bản sao lưu sau khoảng thời gian này để tiết kiệm chi phí lưu trữ cho bạn. Trong bài thực hành này, bạn sẽ giữ nguyên mặc định là **35 ngày**.
      - **Copy to destination - *optional***: Bạn có thể lựa chọn thêm việc nhân bản bản sao lưu của bạn sang một Region khác để tăng khả năng dự phòng. Trong khuôn khổ bài thực hành, chúng ta sẽ không thiết lập tính năng này.
5. Kiểm tra thông tin và chọn **Create**

![2_BackupRuleConfiguration](../../../images/2/2_BackupRuleConfiguration.png?width=90pc)

#### 2. Thiết lập các Resource sẽ sử dụng Backup Plan

Khi bạn gán các resource vào một backup plan, các resource đó sẽ được sao lưu tự động theo thiết lập của backup plan. Bạn có thể gán resource bằng cách sử dụng **Tags** hoặc **Resource ID**.

Chúng ta sẽ tiến hành gán các resourc vào Backup Plan như sau:

1. Truy cập vào **AWS Management Console**, tìm **AWS Backup** trong menu **Services** để truy cập vào **AWS Backup console**.
2. Ở thanh điều hướng, chọn **Backup plans**.
3. Chọn backup plan đã tạo ở trên (ví dụ: sharenote-backup) để vào trang thông tin chi tiết của backup plan.
4. Ở mục **Resource assignments**, chọn **Assign resources**.

![2_AssignResource](../../../images/2/2_AssignResource.png?width=90pc)

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
6. Cuối cùng, chọn **Assign resources**.

![2_AssignResourcePrompt](../../../images/2/2_AssignResourcePrompt.png?width=90pc)
