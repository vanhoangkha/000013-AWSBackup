---
title : "Create S3 Bucket"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Create S3 Bucket

In this section, we will use **CloudFormation** to create resources for the lab. The **CloudFormation** stack will create service resources such as an **EC2 instance**, **SNS Topic**, and **Lambda Function**.

#### Step 1: Download Template

1. First, download the [template CloudFormation and Lambda Function](https://github.com/AWS-First-Cloud-Journey/Backup-Plan/archive/refs/heads/master.zip).

#### Step 2: Create an S3 Bucket

1. Create an **S3 bucket** to store the source data by following these steps:

   - Go to the **AWS Management Console**.
   - Find and select **S3**.

   ![AWS Backup](/images/2-preparation/1.png?featherlight=false&width=90pc)

2. In the **S3** interface, select **Create bucket**.

   ![AWS Backup](/images/2-preparation/2.png?featherlight=false&width=90pc)

3. In the **Create bucket** interface:

   - Enter a **Bucket name**. It must be a unique name; you can choose any name you like.

   ![AWS Backup](/images/2-preparation/3.png?featherlight=false&width=90pc)

   > **Note:** In this workshop, we will use the Singapore region (ap-southeast-1). If you want to use another region, be sure to adjust the region when creating workshop-related resources.

4. Preserve the configuration.

   ![AWS Backup](/images/2-preparation/4.png?featherlight=false&width=90pc)

5. Select **Create bucket**.

   ![AWS Backup](/images/2-preparation/5.png?featherlight=false&width=90pc)

6. Finish creating the **S3 bucket**.

   ![AWS Backup](/images/2-preparation/6.png?featherlight=false&width=90pc)

7. Create an archive folder.

   ![AWS Backup](/images/2-preparation/7.png?featherlight=false&width=90pc)

8. In the folder creation interface:

   - Enter the folder name.
   - Select **Create folder**.

   ![AWS Backup](/images/2-preparation/8.png?featherlight=false&width=90pc)

9. Finish creating the folder.

   ![AWS Backup](/images/2-preparation/9.png?featherlight=false&width=90pc)

10. In the newly created folder, upload the downloaded and unzipped files.

    ![AWS Backup](/images/2-preparation/10.png?featherlight=false&width=90pc)

11. In the **Upload** section:

    - Select **Add files**.
    - Choose the files you want to upload.
    - Select **Upload**.

    ![AWS Backup](/images/2-preparation/11.png?featherlight=false&width=90pc)

12. Finish uploading the files.

    ![AWS Backup](/images/2-preparation/12.png?featherlight=false&width=90pc)

13. Configure permissions for the **S3 bucket**:

    - For **Block public access (bucket settings)**.

    ![AWS Backup](/images/2-preparation/13.png?featherlight=false&width=90pc)

14. Uncheck **Block all public access** and then select **Save changes**.

    ![AWS Backup](/images/2-preparation/14.png?featherlight=false&width=90pc)

15. Confirm and select **Confirm**.

    ![AWS Backup](/images/2-preparation/15.png?featherlight=false&width=90pc)

16. Configure the **Bucket policy**:

    - Select **Edit**.

    ![AWS Backup](/images/2-preparation/16.png?featherlight=false&width=90pc)

17. In the **Edit bucket policy** interface, enter the following code and replace `Bucket-Name` with your **Bucket ARN**.

    ```json
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
                "Resources": [
                    "arn:aws:s3:::Bucket-Name/*"
                ]
            }
        ]
    }
    ```

    ![AWS Backup](/images/2-preparation/17.png?featherlight=false&width=90pc)

18. Select **Save changes**.

    ![AWS Backup](/images/2-preparation/18.png?featherlight=false&width=90pc)

19. Verify that the **Public** permissions are set.

    ![AWS Backup](/images/2-preparation/19.png?featherlight=false&width=90pc)

20. Copy the path information of **lambda_function.zip**.

    ![AWS Backup](/images/2-preparation/20.png?featherlight=false&width=90pc)

21. Copy the **Object URL** information of the file **backup-lab.yaml**.

    ![AWS Backup](/images/2-preparation/21.png?featherlight=false&width=90pc)
