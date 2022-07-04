---
title : "Kiểm tra hoạt động"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Kiểm tra hoạt động

Bản sao lưu nguồn dữ liệu chỉ hữu ích nếu dữ liệu có thể được khôi phục từ nguồn đó. Nếu các bản sao lưu không được kiểm tra, bạn có thể rơi vào tình huống khối lượng công việc của mình bị ảnh hưởng bởi một sự kiện và bạn cần khôi phục dữ liệu từ các bản sao lưu của mình, nhưng bản sao lưu bị lỗi và không thể khôi phục dữ liệu hoặc vượt quá RTO của bạn. Để tránh những trường hợp như vậy, các bản sao lưu đã thực hiện phải luôn được kiểm tra để đảm bảo chúng có thể được sử dụng để khôi phục dữ liệu.

Trong phòng thí nghiệm này, bạn sẽ tận dụng AWS Lambda để tự động kiểm tra tất cả các bản sao lưu đã tạo để đảm bảo khôi phục thành công và xóa mọi tài nguyên đã được tạo trong quá trình kiểm tra khôi phục để tiết kiệm chi phí. Điều này sẽ đảm bảo bạn biết về bất kỳ bản sao lưu bị lỗi nào có thể không sử dụng được để khôi phục dữ liệu từ đó. Tự động hóa quy trình này với thông báo được bật sẽ đảm bảo có chi phí hoạt động tối thiểu và các nhóm Vận hành nhận thức được các trạng thái sao lưu và khôi phục.

Khi kiểm tra khôi phục, điều quan trọng là phải xác định các tiêu chí để khôi phục dữ liệu thành công từ tài nguyên được khôi phục. Điều này sẽ phụ thuộc vào nhiều yếu tố như nguồn dữ liệu, loại dữ liệu, biên độ sai sót, v.v. Các tổ chức và chủ sở hữu khối lượng công việc chịu trách nhiệm xác định tiêu chí thành công này.

EC2 instance được tạo như một phần của phòng thí nghiệm này đang chạy một ứng dụng web đơn giản. Đối với trường hợp sử dụng này, tôi đã xác định rằng việc khôi phục dữ liệu thành công nếu ứng dụng cũng đang chạy trên tài nguyên được khôi phục. Nếu tài nguyên được khôi phục bị thiếu bất kỳ tệp quan trọng nào của ứng dụng, kiểm tra sức khỏe được thực hiện đối với tài nguyên được khôi phục sẽ không thành công, cho biết sự cố với bản sao lưu.

#### Kiểm tra phục hồi
Với mục đích của phòng thí nghiệm này, chúng tôi sẽ mô phỏng hành động được AWS Backup thực hiện khi tạo bản sao lưu nguồn dữ liệu bằng cách tạo bản sao lưu theo yêu cầu để xem liệu bản sao lưu có thành công hay không. Sau khi sao lưu hoàn tất, bạn sẽ nhận được thông báo cho biết rằng công việc sao lưu đã hoàn thành và hàm lambda sẽ được gọi. Hàm Lambda sẽ thực hiện các lệnh gọi API để bắt đầu khôi phục dữ liệu từ bản sao lưu đã được tạo. Điều này sẽ giúp chắc chắn rằng bản sao lưu là tốt. Khi quá trình khôi phục đã hoàn tất, bạn sẽ nhận được một thông báo khác xác nhận điều này và hàm lambda sẽ được gọi lại để dọn dẹp các tài nguyên mới đã được tạo như một phần của quá trình khôi phục. Sau khi quá trình dọn dẹp hoàn tất, bạn sẽ nhận được một thông báo cuối cùng xác nhận việc dọn dẹp.

1. Truy cập **AWS Management Console**


   - Vào giao diện **AWS Backup**
   - Chọn **CREATE AN ON-DEMAND BACKUP**

![AWS Backup](/images/5/0001.png?featherlight=false&width=90pc)

2. Trong phần **RESOURCE TYPE**, chọn **EC2**, dán **Instance ID** từ **Output** của CloudFormation Stack.


   - Trong **BACKUP WINDOW**, chọn **CREATE BACKUP NOW**.
   - Đối với **Backup Vault**, chọn **BACKUP-LAB-VAULT.**
   - Mặc định **default IAM role**
   - Chọn **CREATE ON-DEMAND BACKUP**

![AWS Backup](/images/5/0002.png?featherlight=false&width=90pc)

3. Trong **Jobs**, chọn **Backup jobs**, đợi chuyển sang trạng thái **Completed**

![AWS Backup](/images/5/0003.png?featherlight=false&width=90pc)

4. Chọn **Backup jobs ID**

![AWS Backup](/images/5/0004.png?featherlight=false&width=90pc)

5. Xem chi tiết **Backup jobs**

![AWS Backup](/images/5/0005.png?featherlight=false&width=90pc)

6. Kiểm tra mail đã nhận thông báo.

![AWS Backup](/images/5/0006.png?featherlight=false&width=90pc)

7. Kiểm tra mail về **Restore Test Status**

![AWS Backup](/images/5/0007.png?featherlight=false&width=90pc)

8. Xem thông tin **Restore jobs**, chọn **Restore jobs ID**

![AWS Backup](/images/5/0008.png?featherlight=false&width=90pc)

9. Xem chi tiết **Restore jobs**

![AWS Backup](/images/5/0009.png?featherlight=false&width=90pc)

10. Quay lại giao diện **AWS Management Console**

    - Tìm và chọn **CloudWatch**

![AWS Backup](/images/5/00012.png?featherlight=false&width=90pc)

11. Trong giao diện **CloudWatch**

    - Chọn **Logs**
    - Chọn **Log groups**
    - Chọn **Log group** của bài lab. (**```/aws/lambda/RestoreTestFunction-<YOUR CLOUDFORMATION STACK NAME>```**)

![AWS Backup](/images/5/00013.png?featherlight=false&width=90pc)

12. Trong giao diện **Log groups**

    - Chọn **Log streams**
    - Chọn **Log stream** của bài lab.

![AWS Backup](/images/5/00014.png?featherlight=false&width=90pc)

13. Xem chi tiết **Log Events**

![AWS Backup](/images/5/00015.png?featherlight=false&width=90pc)
