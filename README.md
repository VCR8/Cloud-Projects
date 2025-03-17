# Hosting a Static Website on Amazon S3

This project demonstrates how to host a static website using **Amazon S3**. The website files are stored in an S3 bucket and can be accessed via a public URL.

## Steps to Host a Static Website on S3

### 1. Create an S3 Bucket  
- Logged into **AWS Management Console**.  
- Opened **Amazon S3** service.  
- Created a new bucket (e.g., `my-static-website`).  
- **Disabled Block Public Access** to allow public access.  

### 2. Upload Website Files  
- Uploaded `index.html` and other assets to the S3 bucket.  

### 3. Configure Bucket for Static Website Hosting  
- Opened **Properties** tab → Enabled **Static Website Hosting**.  
- Set `index.html` as the default document.  

### 4. Set Public Permissions  
- Opened the **Permissions** tab → Edited **Bucket Policy**:  

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-static-website-demoprojects/*"
    }
  ]
}

# Creating Azure VM using Cloud Shell
