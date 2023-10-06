---
title : "Kiểm tra hoạt động"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

# Kiểm tra hoạt động

Để đảm bảo tính hữu ích của bản sao lưu dữ liệu, việc kiểm tra sao lưu là điều quan trọng. Nếu không kiểm tra, có thể xảy ra trường hợp dữ liệu không thể khôi phục từ sao lưu. Điều này có thể dẫn đến tình trạng khối lượng công việc bị ảnh hưởng do cần phải khôi phục từ sao lưu, nhưng sao lưu bị lỗi hoặc thời gian khôi phục (RTO) bị vượt quá. Để tránh tình hình này, sao lưu cần phải được kiểm tra thường xuyên để đảm bảo khả năng khôi phục.

Trong phòng thí nghiệm này, AWS Lambda được sử dụng để tự động kiểm tra tất cả sao lưu đã tạo, đảm bảo rằng quá trình khôi phục thành công và tài nguyên tạo trong quá trình kiểm tra sau đó được xóa để tiết kiệm chi phí. Việc tự động hóa quy trình này với thông báo kích hoạt sẽ giúp đảm bảo hoạt động với mức chi phí thấp nhất và các nhóm vận hành có hiểu biết về trạng thái của sao lưu và khôi phục.

Trong quá trình kiểm tra khôi phục, điều quan trọng là phải xác định các tiêu chí cần thiết để khôi phục dữ liệu thành công từ tài nguyên đã được sao lưu. Điều này sẽ phụ thuộc vào nhiều yếu tố như nguồn dữ liệu, loại dữ liệu, mức độ sai sót, và nhiều yếu tố khác. Các tổ chức và người sở hữu khối lượng công việc sẽ chịu trách nhiệm xác định các tiêu chí thành công này.

Ví dụ, trong phòng thí nghiệm này, một EC2 instance đã được tạo và đang chạy một ứng dụng web đơn giản. Trong trường hợp này, tiêu chí khôi phục thành công được xác định bằng việc kiểm tra xem ứng dụng có đang chạy trên tài nguyên đã được khôi phục hay không. Nếu bất kỳ tệp quan trọng nào của ứng dụng bị thiếu trên tài nguyên khôi phục, việc kiểm tra sức khỏe sẽ thất bại, cho biết có sự cố với bản sao lưu.

#### Kiểm tra phục hồi

Trong phạm vi của phòng thí nghiệm này, chúng ta sẽ mô phỏng hành động mà AWS Backup thực hiện khi tạo bản sao lưu nguồn dữ liệu. Đầu tiên, chúng ta sẽ tạo một bản sao lưu theo yêu cầu để kiểm tra xem liệu sao lưu có thành công hay không. Khi bản sao lưu hoàn tất, thông báo sẽ được gửi để báo cáo về việc hoàn thành sao lưu và hàm Lambda sẽ được kích hoạt. Hàm Lambda sẽ thực hiện các lệnh gọi API để bắt đầu quá trình khôi phục từ bản sao lưu. Điều này đảm bảo tính chính xác của sao lưu. Sau khi quá trình khôi phục hoàn tất, một thông báo khác sẽ được gửi để xác nhận việc này và hàm Lambda sẽ được gọi lần nữa để dọn dẹp tài nguyên mới được tạo trong quá trình khôi phục. Khi quá trình dọn dẹp hoàn tất, một thông báo cuối cùng sẽ được gửi để xác nhận việc dọn dẹp.

1. Truy cập vào **AWS Management Console**:

   - Mở giao diện **AWS Backup**
   - Chọn **CREATE AN ON-DEMAND BACKUP**

   ![AWS Backup](/images/5-test/1.png?featherlight=false&width=90pc)

2. Trong phần **RESOURCE TYPE**, chọn **EC2**, sau đó dán **Instance ID** từ phần **Output** của CloudFormation Stack.

   - Trong **BACKUP WINDOW**, chọn **CREATE BACKUP NOW**.
   - Đối với **Backup Vault**, chọn **BACKUP-LAB-VAULT.**
   - Sử dụng vai trò IAM mặc định.
   - Chọn **CREATE ON-DEMAND BACKUP**

   ![AWS Backup](/images/5-test/2.png?featherlight=false&width=90pc)

3. Trong **Jobs**, chọn **Backup jobs**, và chờ cho đến khi trạng thái chuyển sang **Completed**

   ![AWS Backup](/images/5-test/3.png?featherlight=false&width=90pc)

4. Nhấp vào **Backup jobs ID** để xem chi tiết.

   ![AWS Backup](/images/5-test/4.png?featherlight=false&width=90pc)

5. Kiểm tra email để xác nhận thông báo.

   ![AWS Backup](/images/5-test/5.png?featherlight=false&width=90pc)

6. Kiểm tra email liên quan đến **Restore Test Status**.

   ![AWS Backup](/images/5-test/6.png?featherlight=false&width=90pc)

7. Xem thông tin **Restore jobs**, chọn **Restore jobs ID**.

   ![AWS Backup](/images/5-test/7.png?featherlight=false&width=90pc)

8. Xem chi tiết **Restore jobs**.

   ![AWS Backup](/images/5-test/8.png?featherlight=false&width=90pc)

9. Quay lại giao diện **AWS Management Console**:

   - Tìm và chọn **CloudWatch**

   ![AWS Backup](/images/5-test/9.png?featherlight=false&width=90pc)

10. Trong giao diện **CloudWatch**:

    - Chọn **Logs**
    - Chọn **Log groups**
    - Chọn **Log group** của bài lab. (```/aws/lambda/RestoreTestFunction-<YOUR CLOUDFORMATION STACK NAME>```)

    ![AWS Backup](/images/5-test/10.png?featherlight=false&width=90pc)

11. Trong giao diện **Log groups**:

    - Chọn **Log streams**
    - Chọn **Log stream** của bài lab.

    ![AWS Backup](/images/5-test/11.png?featherlight=false&width=90pc)

12. Xem chi tiết **Log Events**.

    ![AWS Backup](/images/5-test/12.png?featherlight=false&width=90pc)

Bằng cách hoàn thành các bước trên, bạn đã triển khai thành công **AWS BACKUP CHO HỆ THỐNG**.
