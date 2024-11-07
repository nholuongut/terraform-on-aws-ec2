# Title: Develop Terraform Modules Locally

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

# Description: Create Terraform Modules locally

# Develop Terraform Modules Locally

## Step-01: Introduction
- How to develop Terraform modules locally ?
- How to leverage and use open source Terraform Modules locally if we don't have access from our organization private networks to Terraform Public Registry ?

## Step-02: Copy templates from  06-AWS-VPC
- Copy `terraform-manifests` from `06-AWS-VPC\06-02-AWS-VPC-using-Terraform\terraform-manifests\v2-vpc-module-standardized`

## Step-03: Download Public Registry Terraform Module 
- Download the VPC module from Terraform Public Registry

## Step-04: Create VPC Local Module
- Create `modules` folder in Terraform Working Directory `terraform-manifests`
- Copy the downloaded VPC module to `modules` folder with module folder name `aws-vpc`
- Remove all other unused or un-required files from this downloaded module. 
- Update the `source` argument in `c4-02-vpc-module.tf`
- Also comment `version` argument
```t
# Create VPC Terraform Module
module "vpc" {
  source  = "./modules/aws-vpc"
  #version = "2.78.0"
  
###  BELOW Terraform code is truncated and will be available in c4-02-vpc-module.tf
```

## Step-05: Execute Terraform Commands
```t
# Terraform Initialize
terraform init
Observation: 
1. Verify the cli output
2. Verify the .terraform\modules folder
3. It will just have the module.json file referencing to local modules folder where aws-vpc module is present

# Terraform Validate
terraform validate

# Terraform Plan
terraform plan

# Terraform Apply
terraform apply -auto-approve
```

## Step-06: Additional Understanding
1. If we want to develop local modules in our organization, don't need to build everything from scratch
2. Analyze what all open source modules available for us and use them and change those as per our requirement. 
3. If we don't relevant module, atleast refer these module related code `main.tf` to get how the advanced level code they write to build such type of re-usable modules


## Step-07: Clean-Up
```t
# Terraform Destroy
terraform destroy -auto-approve

# Delete Files
rm -rf .terraform*
rm -rf terraform.tfstate*
```

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟