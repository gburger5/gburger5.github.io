---
title: S3 Misconfiguration
date: 2024-10-11
categories: [Cybersecurity, Learning, Cloud]
tags: [cybersecurity, learning, cloud]     # TAG names should always be lowercase
---

![S3Image](/assets/images/S3.png)

# S3 Misconfigurations

In the cloud environment, managed services are extremely popular as they take the responsibility off the customer and place it onto the cloud provider. However, confusion about who is responsible for securing certain elements of a service is a cause for vulnerabilities. As cloud environments grow in popularity, there is an increased need for standardized secure practices around the configurations of these managed services. The customer must do their part to create secure policies for their services to protect their data.

The service I am focusing on throughout this post is going to be **Amazon S3**. S3 is an extremely scalable object storage managed by **Amazon Web Services (AWS)**. As mentioned previously, managed services fall in a weird spot on the shared responsibility model as AWS is responsible for the “security of the cloud” and customers are responsible for “security in the cloud.” Customers often fall short of their responsibility as found in a study from Qualys ([LINK HERE](https://www.qualys.com/2023/totalcloud-security-insights/)):

> "31% of S3 buckets are publicly accessible."

This study was done in 2023 and common misconfigurations are still prevalent today, as some companies put priority on getting things up and running quickly rather than the security of their product. This lack of common secure practices leads to easy exploitation. Tools like **Pacu** can be used to easily collect data from buckets. I can understand deep-rooted vulnerabilities that require stringent testing and searching to find being swept under the rug. However, having your data just publicly open for anyone to access is unacceptable.

In order to combat this problem, I believe an offensive-minded approach is best. Thinking like an attacker can help prevent these common vulnerabilities from the start when creating a bucket policy. Setting up basic logging, encryption, and access control is a great start and would turn away a lot of script kiddies from pulling or deleting data from S3. **Multi-factor authentication** is also a must for delete operations inside S3, which prevents any unwanted user from removing data after gaining initial access to the bucket. Using an attacker's mentality and forging a secure bucket policy is key. 

But what if all of your buckets are already created without this security in mind? This is where tooling comes into play.

I am currently working on a tool called **S3 Sentinel** that can scan S3 buckets for these common vulnerabilities. I plan to allow the tool to modify and change the policies in order to make them compliant and effective. Using offensive scanning methodology can allow us to find the easy holes in configuration and prevent script kiddies and professionals alike from picking apart our buckets. During this project, I have used **Terraform** to create "dummy" buckets that display these common vulnerabilities to test with. I am creating this script with **Python** and the **AWS Python SDK Boto3**. Here is a link to the repository: [S3 Sentinel GitHub](https://github.com/gburger5/S3Sentinel).

If you would like to contribute or help automate configuration changes and test other common vulnerabilities, please DM me. I believe creating scanners and automated fixes for these managed services can help fend off a lot of the common attacks that occur. There is still much more work to be done.

---

### Resources:

- [Qualys Study](https://www.qualys.com/2023/totalcloud-security-insights/)
- [S3 Sentinel GitHub](https://github.com/gburger5/S3Sentinel)
