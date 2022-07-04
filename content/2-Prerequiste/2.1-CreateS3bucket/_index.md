---
title : "Create S3 Bucket"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Create S3 Bucket

In this section, we will use **CloudFormation** to create resources for the lab. **CloudFormation** stack will create service resources like **EC2 instance**, **SNS Topic**, and **Lambda Function**

The first step we need to download [template CloudFormation and Lambda Function](https://github.com/AWS-First-Cloud-Journey/Backup-Plan/archive/refs/heads/master.zip)

1. After downloading **[template CloudFormation and Lambda Function](https://github.com/AWS-First-Cloud-Journey/Backup-Plan/archive/refs/heads/master.zip)**

   - We will create a **S3 bucket** to store the source.
   - Go to **AWS Management Console**, find and select **S3**


![AWS Backup](/images/1/0001.png?featherlight=false&width=90pc)

2. In the **S3** interface, select **Create bucket**

![AWS Backup](/images/1/0002.png?featherlight=false&width=90pc)

3. In the **Create bucket** interface

   - Enter **Bucket name** must enter a unique name, you can choose arbitrarily (If the match will lead to an error and cannot initialize the bucket)

![AWS Backup](/images/1/0003.png?featherlight=false&width=90pc)

4. Preserve the configuration.

![AWS Backup](/images/1/0004.png?featherlight=false&width=90pc)

5. Select **Create bucket**

![AWS Backup](/images/1/0005.png?featherlight=false&width=90pc)

6. Finish creating **S3 bucket**

![AWS Backup](/images/1/0006.png?featherlight=false&width=90pc)

7. Make an archive folder

![AWS Backup](/images/1/0007.png?featherlight=false&width=90pc)

8. In the interface create a folder


   - Enter the name **Folder name**
   - Select **Create folder**

![AWS Backup](/images/1/0008.png?featherlight=false&width=90pc)

9. Finish creating a folder

![AWS Backup](/images/1/0009.png?featherlight=false&width=90pc)

10. In the folder just created, execute **Upload** the downloaded and unzipped files.

![AWS Backup](/images/1/00010.png?featherlight=false&width=90pc)

11. In the **Upload** section

    - Select **Add files**
    - Select the files you want to upload.
    - Select **Upload**

![AWS Backup](/images/1/00011.png?featherlight=false&width=90pc)

12. Finish downloading files

![AWS Backup](/images/1/00012.png?featherlight=false&width=90pc)

13. Configure **Permissions** for **S3 bucket**

    - For **Block public access (bucket settings)**

![AWS Backup](/images/1/00013.png?featherlight=false&width=90pc)

14. Uncheck ***Block all public access**

    - Then, select **Save changes**

![AWS Backup](/images/1/00014.png?featherlight=false&width=90pc)

15. Confirm with **confirm** and select **Confirm**

![AWS Backup](/images/1/00015.png?featherlight=false&width=90pc)

16. Then configure **Bucket policy**

    - Select **Edit**

![AWS Backup](/images/1/00016.png?featherlight=false&width=90pc)

17. In the **Edit bucket policy** interface

    - Enter the following code and replace it with your **Bucket ARN**.


```
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

![AWS Backup](/images/1/00017.png?featherlight=false&width=90pc)

18. Select **Save changes**

![AWS Backup](/images/1/00018.png?featherlight=false&width=90pc)

19. Check **Permissions** **Public**

![AWS Backup](/images/1/00019.png?featherlight=false&width=90pc)

20. Copy the path information of **lambda_function.zip**

![AWS Backup](/images/1/00020.png?featherlight=false&width=90pc)

21. Copy the **Object URL** information of the file **backup-lab.yaml**

![AWS Backup](/images/1/00021.png?featherlight=false&width=90pc)