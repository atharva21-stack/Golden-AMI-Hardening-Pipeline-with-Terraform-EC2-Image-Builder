# Automated Golden Image Hardening Pipeline for Security & Compliance in AWS

## **Overview**
This repository provides an end-to-end solution for automating the creation, hardening, and distribution of secure Amazon Machine Images (AMIs) using **AWS EC2 Image Builder** and **Terraform**. The pipeline is designed to ensure that every AMI is up-to-date with the latest patches, meets compliance requirements, and is production-ready. By utilizing **Infrastructure as Code (IaC)**, the process is fully automated, scalable, and enforces consistent security standards across your AWS environments.

---

## **Core Capabilities**
- **Automated AMI Generation**: The pipeline initiates AMI builds based on predefined recipes, using Amazon Linux 2 as the base. This guarantees that all instances launched are aligned with organizational security guidelines.
- **Comprehensive Security Hardening**: Hardened components, such as OS-level security scripts and patch management, are automatically applied to minimize vulnerabilities, enforce encryption, and maintain patch compliance.
- **IAM Permission Boundaries**: Permission boundaries are implemented to restrict privilege escalation and tightly control access, even for users with administrative roles.
- **Terraform-Driven Orchestration**: The entire lifecycle—from image creation to distribution—is managed via **Terraform**, enabling repeatable and consistent deployments across multiple AWS accounts and regions.

---

## **Technical Architecture**

The solution leverages **AWS EC2 Image Builder** for constructing and hardening AMIs, with **Terraform** orchestrating the infrastructure and pipeline automation.

### **Workflow Steps**

1. **Image Recipe Definition**  
   - Specify the base AMI (Amazon Linux 2) and add hardening scripts, security patches, and required software in the recipe file.
2. **Image Building and Hardening**  
   - EC2 Image Builder composes a hardened AMI, ensuring compliance with internal and external standards.
3. **AMI Distribution**  
   - The resulting secure AMI is shared across designated AWS accounts and regions for deployment.
4. **IAM Security Controls**  
   - IAM Permission Boundaries ensure only authorized roles can launch the hardened AMIs, reducing the risk of unauthorized privilege escalation.
5. **Automated Deployment via Terraform**  
   - Terraform modules manage the provisioning and automation of the entire pipeline, allowing easy scaling across regions and accounts.
6. **Compliance Monitoring**  
   - AWS CloudWatch and AWS Config continuously monitor the hardened AMIs to ensure ongoing compliance and security posture.

---

## **Project Structure**
## **Project Structure**

```
├── terraform/
│   ├── main.tf                  # Terraform configs for infrastructure, IAM roles, and pipeline automation
│   ├── variables.tf             # Variables for region, AMI IDs, and other parameters
│   ├── outputs.tf               # Outputs such as created AMI IDs
│   ├── policies/
│   │   ├── iam_permission_boundary.json   # IAM Permission Boundary policy restricting privileges
│   └── modules/                
│       └── image_builder.tf     # EC2 Image Builder configurations
├── scripts/
│   └── install_packages.sh      # Script for installing security tools and applying patches
├── configs/
│   └── ec2-image-recipe.json    # Image Builder recipe defining base AMI and hardening components
```


## **Getting Started**

1. **Clone the repository**  
git clone https://github.com/your-username/golden-image-hardening-pipeline.git
cd golden-image-hardening-pipeline


2. **Configure the pipeline**  
- Update `main.tf` with your AWS region, account info, and other settings.  
- Adjust IAM Permission Boundaries and hardening scripts as per your security policies.

3. **Deploy the pipeline**  
- Initialize Terraform:  
  ```
  terraform init
  ```
- Apply the configuration:  
  ```
  terraform apply
  ```

4. **Monitor the pipeline**  
- The pipeline will automatically create and harden AMIs.  
- Track progress via AWS Console or CLI:  
  ```
  aws imagebuilder list-image-pipelines
  ```

---

## **Contributing**

Contributions are welcome! Please open an issue for suggestions or submit a pull request. For major changes, start a discussion first.

---
