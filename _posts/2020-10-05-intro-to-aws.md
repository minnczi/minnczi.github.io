---
layout: post
title: Intro to AWS
subtitle: Basic Concepts and Terminologies for AWS
categories: [githubblog, korean]
tags: [jekyll, ruby, github]
---

### AWS Identity and Access Management

- **Managed policies:** Policies shared among users and/or groups that are prebuilt either by AWS or an administrator within the AWS account.
  - When it's updated, the changes to this policy are immediately applied for all users and groups to which it's attached.
  - It's like using css to define styling in HTML
- **Inline policies:** Policies assigned to just one user or group that are typically used in one-off situations.
  - It's like using inline HTML styling



- **Bucket**: An Amazon S3 bucket is a public cloud storage resource available in Amazon Web Services' (AWS) Simple Storage Service (S3), an object storage offering.



### S3 Lifecycle Policy

**Glacier**: It's like back harddrive

- Glacier is used to effectively manage storage space
- Bulk of data will be moved to Glacier
- Unused data will be automatically deleted after certain period to save storage space in the cloud

![Image Alt Text](/assets/images/glacier-diagram.png)


**3 Steps in Access Control**

- Identification
- Authentication
  - Knowledge based: ex. password
  - Ownership based: ex. OTP, 주민등록증
  - 
- Authorization



- Redirect
- Forward

directory listing



