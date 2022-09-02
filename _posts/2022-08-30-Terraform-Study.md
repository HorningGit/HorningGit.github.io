---
layout: post
title: Terraform Providers
subtitle: (Studying Terraform w/ Deployments to AWS)
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/terraform.png
share-img: /assets/img/path.jpg
tags: [terraform, aws]
---

Tonight I was able to finish some documentation for a Terraform lab. It was my first time using Terraform with AWS resources tonight, and I had a really good time. Here is a link to Terraform's official [AWS registry](https://registry.terraform.io/providers/hashicorp/aws/latest). The differences in the various Terraform blocks are starting to make a lot more sense to me (ie. providers, resource, etc.)

Here is snipit of my Terraform code I desployed to AWS tonight!

```terraform
# Horning East AWS Region
provider "aws" {
  alias  = "us-east-1"
  region = "us-east-1"
}

# Horning West AWS Region
provider "aws" {
  alias  = "us-west-2"
  region = "us-west-2"
}

# Horning SNS Topic_1
resource "aws_sns_topic" "topic-us-east" {
  provider = aws.us-east-1
  name     = "topic-us-east"
}

# Horning SNS Topic_2
resource "aws_sns_topic" "topic-us-west" {
  provider = aws.us-west-2
  name     = "topic-us-west"
}
```
