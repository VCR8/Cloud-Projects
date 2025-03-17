# Hosting a Virtual Machine on Microsoft Azure using Cloud Shell

This project demonstrates how to create and manage a Virtual Machine (VM) using **Microsoft Azure**. The VM is provisioned using Azure CLI in **Azure Cloud Shell**.

## Steps to Create an Azure VM

### 1. Create a Resource Group  
- Logged into **Azure Portal**.  
- Opened **Azure Cloud Shell**.  
- Created a new resource group:  
  ```bash
  az group create --name MyResourceGroup --location eastus
  ```

### 2. Create a Virtual Machine  
- Used Azure CLI to create a VM:  
  ```bash
  az vm create \
      --resource-group MyResourceGroup \
      --name MyVM \
      --image Ubuntu2204 \
      --admin-username azureuser \
      --generate-ssh-keys
  ```

### 3. Verify VM Deployment  
- Listed all running VMs:  
  ```bash
  az vm list -d -o table
  ```
![image](https://github.com/user-attachments/assets/2a227a9d-fe84-4b71-86de-0b8115cc6d2a)

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

