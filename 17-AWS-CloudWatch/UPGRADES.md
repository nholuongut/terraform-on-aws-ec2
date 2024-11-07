# Terraform Manifest Upgrades

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

## Step-01: c14-03-cloudwatch-alb-alarms.tf
```t
# Before
  dimensions = {
    LoadBalancer = module.alb.lb_arn_suffix
  }

# After
  dimensions = {
    LoadBalancer = module.alb.arn_suffix # UPDATED 
  }  
```

## Step-02: c14-05-cloudwatch-synthetics.tf
```t
# Create S3 Bucket
resource "aws_s3_bucket" "cw_canary_bucket" {
  bucket = "cw-canary-bucket-${random_pet.this.id}"
  #acl    = "private" # UPDATED 
  force_destroy = true

  tags = {
    Name        = "My bucket"
    Environment = "Dev"
  }
}
# Create S3 Bucket Ownership control - ADDED NEW
resource "aws_s3_bucket_ownership_controls" "example" {
  bucket = aws_s3_bucket.cw_canary_bucket.id
  rule {
    object_ownership = "BucketOwnerPreferred"
  }
}
# Create S3 Bucket ACL - ADDED NEW
resource "aws_s3_bucket_acl" "example" {
  depends_on = [aws_s3_bucket_ownership_controls.example]
  bucket = aws_s3_bucket.cw_canary_bucket.id
  acl    = "private"
}
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