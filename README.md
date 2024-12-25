# AWS Cost Optimization | Strategies & Implementation

| Created     |    Version   | Author | Comment | Reviewer | Date |
|:---:|:---:|:---:|:-----:|:-----:|:----:|
| 23-12-2024  | V1   | Chander kant | Internal Review |  | |
| 23-12-2024  | V1   | Chander kant | L0 | |  |
|23-12-2024 | V2 | Chander kant | L1  |  | |
| | V3 |  Chander kant | L2  | ||

---

 ## Table Of Contents
 - [Introduction](#Introduction)
 - [AWS Cost](#AWS-Cost)
   - [What is AWS Cost](#What-is-AWS-Cost)
   - [AWS Bill Typically Consists Of](#AWS-Bill-Typically-Consists-Of)
   - [Why we Need Cost Optimization](#Why-we-Need-Cost-Optimization)
 - [AWS Services In Our Project](#AWS-Services-In-Our-Project)
   - [Services and Their Charges](#Services-and-Their-Charges)
   - [Types of Cost](#Types-of-Cost)
 - [Strategies](#Strategies)
   - [For Saving the AWS cost](#For-Saving-the-AWS-cost) 
 - [Implementation](#Implementation)
   - [How We can save Our Cost](#How-We-can-save-Our-Cost) 
 - [Conclusion](#Conclusion)
 - [Contact Information](#Contact-Information)
 - [Refrences](#Refrences)

 ---

 ## Introduction
This document aims to provide an overview of strategies, best practices to help organizations manage their AWS costs effectively. AWS Cost Optimization is the process of identifying, analyzing, and reducing  unnecessary cloud spend while maintaining performance, scalability, and availability. By optimizing costs, organizations can achieve a more cost-efficient AWS environment, aligning their usage with business goals and operational needs. 

## AWS cost
#### What is AWS Cost
---
 AWS (Amazon Web Services) offers a variety of cloud computing services, and its pricing depends on the specific services you use, how much you use them, and the pricing model you choose. The cost structure for AWS is complex because it offers many different types of services, each with its own pricing model. Below is the breakdown of AWS Cost model
| **Pricing Model**      | **Description**                                                                                         | **Use Case**                                                     |
|------------------------|---------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| **On-Demand Pricing**   | Pay for compute or storage by the hour/second with no upfront cost.                                      | Suitable for unpredictable workloads or short-term usage.       |
| **Reserved Pricing**    | Commit to resources for 1 or 3 years for a discounted rate. Available for EC2, RDS, etc.                | Best for predictable, long-term workloads.                      |
| **Spot Pricing**        | Purchase unused capacity at discounted rates, up to 90% off. Can be interrupted by AWS.                | Ideal for flexible, fault-tolerant workloads.                   |
| **Savings Plans**       | Commit to consistent usage (in $/hr) for 1 or 3 years for a discount. Available for EC2, Lambda, etc.   | Best for workloads with predictable resource usage.             |
| **Free Tier**           | Free limited resources for new users (e.g., 750 hrs of t2.micro EC2 per month, 5GB S3 storage).         | Great for experimentation or small-scale usage.                |
| **Pay-as-You-Go**       | Pay for actual usage without any upfront cost. Most services use this model.                            | Flexible, variable usage with no commitment.                    |
| **Dedicated Hosting**   | Pay for dedicated physical servers. For customers needing physical isolation or specific compliance.    | For workloads needing isolated, dedicated physical hardware.    |
| **Cost Per Request**    | Charge based on the number of requests or transactions (e.g., API calls, database queries).             | Common for serverless services like Lambda, API Gateway, etc.   |



#### AWS Bill Typically Consists Of

---


| **Cost Type**           | **Description**                                                                                                                                          | **Key Factors**                                                                                             |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| **Compute Costs**        | Charges related to running instances (EC2), containers, and serverless functions (Lambda).                                                            | Based on the type and size of instances used, as well as the duration for which they are running.            |
| **Storage Costs**        | Costs associated with storing data in AWS services like Amazon S3, Elastic Block Store (EBS), and Glacier.                                                 | Varies depending on the storage type (S3, EBS, Glacier), amount of data stored, and the frequency of access.  |
| **Data Transfer Costs**  | Charges for data transfer between AWS services and regions. Egress (data leaving AWS) often incurs additional costs.                                      | Dependent on the volume of data transferred between regions, to/from the internet, and across services.       |



 #### Why we Need Cost Optimization 
 ---
We need Cost optimization because of this is the process of efficiently managing and reducing cloud expenses while maintaining performance, scalability, and reliability. It involves analyzing cloud usage, identifying inefficiencies, and implementing strategies (such as right-sizing resources, selecting the most cost-effective pricing models, and automating scaling) to minimize unnecessary costs and maximize the value of cloud services.


---

## AWS Services In Our Project
#### Services and Their Charges
---


 As we  know  that  AWS  provides a wide range of services to fullfill the goal of need to complete the project , here below are the some services of AWS that we are  using in our project.Below are some details of the services
 | **AWS Service**        | **Type of Service**           | **Charges**                                                                                          |
|------------------------|-------------------------------|------------------------------------------------------------------------------------------------------|
| **VPC (Virtual Private Cloud)** | Networking/Infrastructure | Charges based on data transfer, VPN connections, NAT gateways, and the number of VPC endpoints used.  |
| **EC2 (Elastic Compute Cloud)** | Compute                   | Charges based on instance type, running time (per second or hour), and additional resources like EBS storage and data transfer. |
| **Load Balancers**      | Networking/Compute            | Charges based on the number of load balancer hours used and the amount of data processed. Different pricing for Application Load Balancer, Network Load Balancer, and Classic Load Balancer. |
| **Auto Scaling Groups** | Compute/Automation            | No direct cost for Auto Scaling itself. Charges are based on EC2 instances that are launched and terminated as part of scaling activities. |
| **S3 (Simple Storage Service)** | Storage                   | Charges based on data storage (per GB), data retrieval requests, and data transfer. Also, pricing depends on the S3 storage class used (Standard, Intelligent-Tiering, Glacier, etc.). |
| **Route 53**            | DNS & Networking              | Charges based on the number of hosted zones, DNS queries, and health checks.                         |
| **EBS (Elastic Block Store)** | Storage                   | Charges based on the amount of storage provisioned, IOPS (input/output operations), and data transfer between EC2 and EBS. |
| **IAM (Identity and Access Management)** | Security/Management    | No direct charges for IAM itself. However, there may be costs for related resources, such as access to AWS services or API calls. |

---

## Types of Cost


| **Cost Type**                | **Description**                                            | **Example Services**                               | **Billing Details**                                 |
|------------------------------|------------------------------------------------------------|---------------------------------------------------|-----------------------------------------------------|
| **On-Demand**                 | Pay for resources used without long-term commitment.       | EC2 instances, Load Balancers, S3 storage         | Billed based on usage per hour, second, or GB stored. |
| **Reserved**                  | Upfront payment for long-term use at a discounted rate.    | EC2 Reserved Instances, RDS Reserved Instances     | Billed upfront for a fixed term (1 or 3 years).     |
| **Spot**                      | Reduced-cost EC2 instances based on unused capacity.      | EC2 Spot Instances                                | Billed based on duration running, typically much lower than on-demand pricing. |
| **Data Transfer**             | Costs for data transferred between regions or out of AWS.  | EC2, VPC, S3, Load Balancers, Route 53            | Charged per GB for outbound data transfer.          |
| **Storage**                   | Charges based on data stored in services like S3 or EBS.   | S3, EBS                                            | Billed per GB of data stored.                       |
| **Request/Operation**         | Costs for API calls, DNS queries, or data requests.       | S3 (PUT, GET, LIST requests), Route 53 (DNS queries), EC2 (API calls) | Charged based on the number of requests or operations performed. |
| **Elastic IP**                | Charges for unused Elastic IPs or if not associated with EC2. | EC2                                               | Charged if the Elastic IP is not associated with a running instance. |
| **License and Features**      | Costs for licensed software and additional services.      | EC2 (Windows, other software licenses), RDS (Oracle) | Billed on top of base service cost for licenses or features used. |
| **Support**                   | AWS support plan charges based on the level of service.   | AWS Support                                       | Billed monthly based on your AWS usage, depending on the support plan chosen. |
| **Provisioned and Reserved**  | Reserved capacity commitments for long-term use.          | EC2 Reserved Instances, RDS Reserved Instances     | Billed upfront for a set term, offering lower rates. |

---


## Strategies
Here are the some principle tips to reduce the AWS bill 
#### For Saving the AWS Cost
---
| **Strategy**                             | **Description**                                                                                  | **Key Benefits**                                                         | **Tools/Recommendations**                           |
|------------------------------------------|--------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------|
| **Rightsizing EC2 Instances**            | Adjust instance types based on actual usage (CPU, memory, network).                              | Reduces overspending by avoiding overprovisioning.                        | AWS Trusted Advisor, Auto-scaling                  |
| **Reserved Instances & Savings Plans**   | Commit to specific instances (RIs) or usage (Savings Plans) for long-term savings.               | Up to 72% savings with RIs; more flexibility with Savings Plans.          | Reserved Instances, Savings Plans                   |
| **Leverage Spot Instances**              | Use Spot Instances for flexible workloads that can handle interruptions.                          | Save up to 90% off regular EC2 pricing.                                  | Spot Fleet, 2-minute interruption warning           |
| **Optimize Storage Costs**               | Use appropriate S3 storage classes and manage EBS volumes.                                        | Reduces costs by choosing the right storage class for your needs.        | S3 Lifecycle Policies, EBS Cleanup                 |
| **Reduce Data Transfer Costs**           | Keep data transfers within the same region and use CDNs to reduce cross-region transfers.        | Reduces costs by minimizing data movement across regions.                | Amazon CloudFront, Regional consolidation          |
| **Utilize AWS Lambda**                   | Use Lambda for event-driven or sporadic workloads instead of running EC2 instances 24/7.         | Pay only for compute time used, ideal for bursty workloads.              | AWS Lambda                                          |
| **Monitor and Optimize with Cost Management Tools** | Use AWS’s built-in tools to track, manage, and optimize AWS usage and costs.                     | Helps monitor spending and optimize usage.                               | AWS Budgets, AWS Cost Explorer, Tags               |
| **Review Unused and Idle Resources**     | Regularly clean up unused resources (Elastic IPs, unattached EBS volumes, idle RDS instances).   | Reduces costs by eliminating idle resources.                             | AWS Trusted Advisor                                 |

Here the **AWS Trusted Advisor** is a service offered by Amazon Web Services (AWS) that provides real-time guidance to help you provision your resources following best practices. It helps you optimize your AWS environment by offering recommendations.

---

## Implementation

#### How We can save Our Cost

---
This is a comprehensive guide to cost optimization techniques for various AWS services, focusing on services like VPC, EC2, Load Balancers, Auto Scaling, S3, Route 53, EBS, and IAM. It also includes region considerations to help make cost-effective decisions for your project.

| **Service**                  | **Cost Optimization Techniques**                                                                                      | **Region Considerations**                                                                                 |
|------------------------------|------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| **VPC & Its Components**      | - **Use Private Subnets** for internal resources. <br> - **Choose NAT Instance** over **NAT Gateway** (if traffic is low). <br> - **Use VPC Peering** instead of **Transit Gateway** to reduce costs. <br> - **Avoid over-provisioning VPCs and subnets.** | - **US East (N. Virginia)**, **US West (Oregon)**: Cost-effective for VPC services. <br> - Consider latency and compliance requirements. |
| **EC2 & Its Components**      | - **Choose the right EC2 instance types** using **Compute Optimizer**. <br> - **Use Spot Instances** for non-critical workloads. <br> - **Utilize Reserved Instances** or **Savings Plans** for predictable workloads. <br> - **Implement Auto Scaling** based on actual demand. <br> - **Regularly right-size instances** based on usage. | - **US East (N. Virginia)**, **EU (Ireland)**: Typically cheaper for EC2 services. <br> - Consider proximity to your users to reduce data transfer costs. |
| **Load Balancers**            | - **Use ALB** for HTTP/HTTPS traffic, and **NLB** for low-latency, high-performance TCP/UDP traffic. <br> - **Consolidate Load Balancers** where possible to reduce costs. | - **US East (N. Virginia)**, **US West (Oregon)**: Generally cheaper for load balancing services. |
| **Auto Scaling Groups**       | - **Define scaling policies** based on actual usage. <br> - **Schedule scaling actions** during predictable demand times. | - Auto Scaling is mostly cost-effective across regions. However, use cheaper regions for underlying instance types (e.g., **US East (N. Virginia)**). |
| **S3 (Storage)**              | - **Use S3 Intelligent-Tiering** or **S3 Glacier** for infrequent access. <br> - **Implement Lifecycle Policies** to transition data to cheaper storage. <br> - **Use S3 Transfer Acceleration** selectively to balance cost and performance. | - **US East (N. Virginia)**: Cost-effective for storage services. <br> - Choose regions with low storage costs and minimize data transfer costs. |
| **Route 53 (DNS)**            | - **Consolidate Hosted Zones**. <br> - **Use Simple Routing** if advanced routing isn’t required. <br> - **Monitor DNS queries** to avoid excessive charges. | - Route 53 pricing is generally consistent across regions, but proximity to users reduces data transfer costs. |
| **EBS (Elastic Block Store)** | - **Choose the appropriate EBS volume type** (e.g., **GP3** for cost savings over **GP2**). <br> - **Regularly take snapshots** and delete unused ones. <br> - **Use automated tiering** to optimize storage. <br> - **Reduce IOPS** if high performance isn’t necessary. | - **US East (N. Virginia)**, **US West (Oregon)**: Lower EBS costs in these regions. |
| **IAM (Identity & Access Management)** | - **Ensure users have least privileged access.** <br> - **Use IAM roles and policies** instead of direct permissions for better cost control. <br> - **Utilize IAM Access Analyzer** to review and refine permissions. | - IAM pricing is the same across all AWS regions. Focus on managing access effectively to avoid unnecessary costs. |
| **General Cost Optimization** | - **Use AWS Cost Explorer** and **AWS Budgets** to monitor costs and usage. <br> - **Consolidate billing** using **AWS Organizations** for potential volume discounts. <br> - **Enable CloudWatch monitoring** to track resource utilization and adjust accordingly. <br> - **Consider purchasing Reserved Instances** or **Savings Plans** for predictable workloads. | - **US East (N. Virginia)**, **US West (Oregon)**: Ideal for low-cost services across many AWS offerings. |


By applying these optimization strategies, you can reduce AWS costs while maintaining the performance and scalability of your project.

---

## Conclusion
To wrap things up, cost optimization on AWS boils down to understanding your usage and making smart adjustments. From rightsizing instances to leveraging tools like Savings Plans and Spot Instances, these strategies can make a real difference in reducing your cloud bill. Regularly reviewing your AWS costs is key—staying proactive will help you avoid surprises. Start small, stay consistent, and you’ll keep those cloud expenses in check without sacrificing performance.

---

## Contact Information

|    NAME           |   Email Address                       |
|:-----------------:|:-------------------------------------:|
|Chander Kant| 	chanderkant.soni.snaatak@mygurukulam.co

---

## Refrences

|Link|Description|
|---|---|
|[Link](https://opstree.com/blog/2024/09/20/cost-optimization-in-aws-tips-for-reducing-your-cloud-bill/)|Document |
|[Link](https://aws.amazon.com/blogs/compute/10-things-you-can-do-today-to-reduce-aws-costs/)|Official Document|

 ---

 
