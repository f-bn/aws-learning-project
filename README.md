<p><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1d/AmazonWebservices_Logo.svg/2560px-AmazonWebservices_Logo.svg.png" alt="aws-logo" title="aws" align="top" height=120 /></p>

*Amazon Web Services, Inc. (AWS) is a subsidiary of Amazon that provides on-demand cloud computing platforms and APIs to individuals, companies, and governments, on a metered pay-as-you-go basis. These cloud computing web services provide distributed computing processing capacity and software tools via AWS server farms - Wikipedia*

### General informations

This repository contains various configuration artefacts for a personal Amazon Web Services learning project.

**References**
  - AWS : https://aws.amazon.com/
  - Terraform : https://www.terraform.io/
  - Packer : https://www.packer.io/
  - Fedora : https://getfedora.org/
  
### The project

**AWS**

The objective of the project is to host a Wordpress-based web solution for a company, the *FBN Corp*, on a public cloud platform. For this project, we have chosen to use ***Amazon Web Services***. We need to use, at least, the following AWS services to meet the company's needs :
  - **EC2** to host the Wordpress application
  - **VPC** to manage public and private networking
  - **Route53** to manage DNS
  - **RDS** for the database backend (we will use PostgreSQL :heart:)
  - **S3** to store the various company assets (videos, pictures...)
  - **ELB** as a front load-balancer to distribute load on the EC2 Wordpress machines
  - **IAM** to manage security for the resources and human accesses
  - **CloudWatch** for the monitoring (metrics, alerting)
  - **ASG** (in tandem with CloudWatch) to manage auto-scaling of the EC2 resources
  - **AWS Backups** for the backups, this could be useful who knows

 ***Note 1** : Other AWS services can be used if needed depending on the project needs evolution*<br/>
 ***Note 2** : For this first project, we will limit ourselves to a deployment on a single region with several Availability Zones (AZ)*

*< insert infrastructure schema >*

**Infrastructure-as-Code (Terraform)**

Regarding the deployment, we have chosen to use Terraform to provision the infrastructure. The Terraform manifests are hosted on this GitHub repository and the `tfstate` will be stored on an internal PostgreSQL database outside of AWS.

**OS provisionning (Linux)**

Since we will use EC2 virtual machines, we will need to configure various system components, the web service by itself, but also the satellite elements around it (i.e application metrics and logs...). The deployment of these EC2 instances must be done in the most industrial way possible, some options are to be evaluated:
  - Use of Hashicorp Packer to build golden AMIs and store them as ***Launch Templates*** for **ASG**
  - Use of Cloud-Init to provision instances on first boot
  - Use of configuration management tools such as Ansible (in *pull-mode*)
  
Regarding the EC2 operating system, we will use **Fedora Linux** with SELinux in enforced mode.
