Step-by-Step Guide to Host a Static Website on AWS S3
Follow these steps to deploy your index.html file and host your static website.

Step 1: Log in to the AWS Management Console

First, log in to your AWS account.

Step 2: Create an S3 Bucket

Navigate to the S3 service from the search bar or the services list.

Click on Create bucket.

Give your bucket a globally unique name (e.g., arya-vedha-website-2024).

Choose the AWS Region where you want to host your website.

Under Object Ownership, make sure to enable ACLs enabled.

Under Block Public Access settings for this bucket, uncheck the box that says "Block all public access" and acknowledge the warning. This is necessary to make your website publicly accessible.

Leave all other settings as default and click Create bucket.

Step 3: Upload Your Website Files

Click on the name of the bucket you just created.

Click the Upload button.

Drag and drop your index.html file into the upload area or click Add files.

Click Upload to start the process.

Step 4: Enable Static Website Hosting

In your bucket, go to the Properties tab.

Scroll down to the Static website hosting section and click Edit.

Select Enable and choose Host a static website.

For the Index document, type index.html.

For the Error document, you can also type index.html or leave it blank for now.

Click Save changes.

Step 5: Edit the Bucket Policy

Go to the Permissions tab of your bucket.

Scroll down to the Bucket policy section and click Edit.

Paste the following policy into the editor, replacing your-bucket-name with the actual name of your bucket. This policy allows anyone to view the objects in your bucket.
```bash
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
            "Resource": [
                "arn:aws:s3:::your-bucket-name/*"
            ]
        }
    ]
}
```
---
Click Save changes.

Step 6: Access Your Website

Go back to the Properties tab.

Scroll down to the Static website hosting section.

You will see a URL under "Bucket website endpoint". Click this URL to view your live website.
