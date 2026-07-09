# 🚀 Terraform AWS S3 Bucket Automation

Welcome to my Terraform + AWS project! 🎉

In this project, I learned how to use **Terraform Infrastructure as Code (IaC)** to automatically create and manage an **Amazon S3 bucket**.

Instead of manually creating AWS resources from the AWS Console, Terraform allows us to write code that describes our infrastructure. Terraform then creates the resources automatically.

This approach is widely used by **DevOps Engineers, Cloud Engineers, DevSecOps Engineers, and Platform Engineers** because it makes infrastructure faster, repeatable, and less error-prone.

---

# 📌 Project Overview

In this project, we will:

✅ Install Terraform  
✅ Configure AWS CLI credentials  
✅ Connect Terraform with AWS  
✅ Create an AWS S3 bucket using Terraform  
✅ Secure the S3 bucket from public access  
✅ Upload files to S3 using Terraform  
✅ Manage AWS infrastructure using code  

---

# 🏗️ Technologies Used

| Technology | Purpose |
|------------|---------|
| Terraform | Infrastructure as Code tool |
| AWS | Cloud platform |
| Amazon S3 | Object storage service |
| AWS CLI | Connect terminal with AWS |
| IAM | Manage AWS permissions |

---

# 💡 What is Terraform?

Terraform is an **Infrastructure as Code (IaC)** tool created by HashiCorp.

It allows us to create and manage cloud resources using configuration files instead of manually clicking in the cloud console.

For example, instead of manually creating:

- S3 Buckets
- EC2 Instances
- VPC Networks
- Databases

We write Terraform code, and Terraform creates them automatically.

### Benefits of Terraform:

✅ Automation  
✅ Reduces human errors  
✅ Infrastructure can be reused  
✅ Easy collaboration with Git  
✅ Supports AWS, Azure, Google Cloud, and more  

---

# 💡 What is Infrastructure as Code (IaC)?

Infrastructure as Code means managing cloud infrastructure using code.

Instead of doing this:

```
AWS Console → Click → Create Resource → Configure Settings
```

We do this:

```
Terraform Code → terraform apply → AWS Creates Resource
```

The infrastructure configuration can be stored in GitHub, shared with teams, and recreated anytime.

---

# 📂 Project Structure

```
terraform-s3-project/
│
├── main.tf
├── terraform.tfstate
├── terraform.tfstate.backup
└── README.md
```

---

# 🛠️ Step 1: Install Terraform

Download Terraform from the official website:

https://developer.hashicorp.com/terraform/downloads

For mac copy and paste in terminal

```bash
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```



Check Terraform installation:

```bash
terraform version
```

Example output:

```
Terraform v1.x.x
```

If you see the version, Terraform is installed successfully.

---

# ☁️ Step 2: Configure AWS CLI

Terraform needs permission to communicate with AWS.

First install AWS CLI.

Check AWS CLI installation:

```bash
aws --version
```

Example:

```
aws-cli/2.x.x
```

---

# 🔑 Configure AWS Credentials

Run:

```bash
aws configure
```

Enter:

```
AWS Access Key ID
AWS Secret Access Key
AWS Region
Default output format
```

Example:

```
AWS Access Key ID: ********
AWS Secret Access Key: ********
Region: us-east-1
Output format: json
```

Now Terraform can authenticate with AWS.

---

# 📁 Step 3: Create Terraform Project

Create a project folder:

```bash
mkdir terraform-s3-project
```

Move inside the folder:

```bash
cd terraform-s3-project
```

Create Terraform configuration file:

```bash
touch main.tf
```

---

# 📝 Step 4: Create Terraform Configuration

Open:

```
main.tf
```

Add the following Terraform code:

```hcl
provider "aws" {

  region = "us-east-1"

}


resource "aws_s3_bucket" "my_bucket" {

  bucket = "my-terraform-demo-bucket-123456"

}


resource "aws_s3_bucket_public_access_block" "my_bucket_public_access_block" {

  bucket = aws_s3_bucket.my_bucket.id


  block_public_acls       = true

  ignore_public_acls      = true

  block_public_policy     = true

  restrict_public_buckets = true

}
```

---

# 🔍 Understanding Terraform Code

## Provider Block

```hcl
provider "aws"
```

This tells Terraform:

"Use AWS as my cloud provider."

---

## Resource Block

```hcl
resource "aws_s3_bucket"
```

This creates an S3 bucket.

Terraform resources represent cloud services like:

- S3
- EC2
- VPC
- RDS

---

## Public Access Block

```hcl
aws_s3_bucket_public_access_block
```

This protects the bucket by blocking public access.

Security settings:

```
block_public_acls = true
ignore_public_acls = true
block_public_policy = true
restrict_public_buckets = true
```

---

# 🚀 Step 5: Initialize Terraform

Run:

```bash
terraform init
```

What happens?

Terraform will:

- Download AWS provider
- Prepare the project
- Create required Terraform files

---

# 🔎 Step 6: Check Terraform Plan

Run:

```bash
terraform plan
```

Terraform shows:

- Resources that will be created
- Resources that will change
- Resources that will be deleted

Example:

```
Plan: 2 to add, 0 to change, 0 to destroy
```

---

# 🏗️ Step 7: Create S3 Bucket

Apply Terraform configuration:

```bash
terraform apply
```

Terraform will ask:

```
Do you want to perform these actions?
```

Type:

```
yes
```

Terraform will create:

✅ S3 Bucket  
✅ Security configuration  

---

# ✅ Verify S3 Bucket

Go to:

AWS Console → S3 → Buckets

You should see your new bucket.

---

# 📤 Upload File to S3 Using Terraform (Optional)

Terraform can also upload objects.

Example:

```hcl
resource "aws_s3_object" "upload_file" {

  bucket = aws_s3_bucket.my_bucket.id

  key    = "example.txt"

  source = "example.txt"

}
```

Run:

```bash
terraform apply
```

Terraform uploads the file automatically.

---

# 🗑️ Delete Resources

When finished, remove AWS resources to avoid charges.

Run:

```bash
terraform destroy
```

Confirm:

```
yes
```

Terraform will delete the S3 bucket and related resources.

---

# 📚 Important Terraform Commands

| Command | Purpose |
|-|-|
| terraform init | Initialize Terraform project |
| terraform plan | Preview changes |
| terraform apply | Create/update resources |
| terraform destroy | Delete resources |
| terraform version | Check Terraform version |
| terraform validate | Check configuration errors |
| terraform fmt | Format Terraform code |

---

# 🎯 What I Learned

After completing this project, I learned:

✅ How Infrastructure as Code works  
✅ How Terraform communicates with AWS  
✅ How to automate AWS resource creation  
✅ How to create and secure S3 buckets  
✅ How DevOps teams manage cloud infrastructure  

---

# 🚀 Future Improvements

Possible improvements:

- Add Terraform variables
- Use Terraform modules
- Store Terraform state remotely using S3 backend
- Add CI/CD pipeline using GitHub Actions
- Automate more AWS services like EC2 and VPC

---

# 👨‍💻 Author

**Mudasir Ahmad**

Cloud | DevOps | AWS | Terraform Projects
