<p><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1d/AmazonWebservices_Logo.svg/2560px-AmazonWebservices_Logo.svg.png" alt="aws-logo" title="aws" align="top" height=120 /></p>

*Amazon Web Services, Inc. (AWS) is a subsidiary of Amazon that provides on-demand cloud computing platforms and APIs to individuals, companies, and governments, on a metered pay-as-you-go basis. These cloud computing web services provide distributed computing processing capacity and software tools via AWS server farms - Wikipedia*

### General informations

This repository contains various configuration artefacts for a personal Amazon Web Services learning project.

**References**
  - AWS : https://aws.amazon.com/
  - Terraform : https://www.terraform.io/
  
### The project

The objective of the project is to host a Wordpress-based web solution for a company, the *FBN Corp*, at a public cloud provider. For this project, we have chosen to use Amazon Web Services. We need to use, at least, the following AWS services to meet the company's needs :
  - **EC2** to host the Wordpress application
  - **VPC** to manage public and private networking
  - **Route53** to manage DNS
  - **RDS** for the database backend (we will use PostgreSQL :heart:)
  - **S3** to store the various company assets (videos, pictures...)
  - **ELB** as front load-balancer to distribute load on the Wordpress machines
  - **IAM** to manage security for the resources and human accesses
  - **CloudWatch** for the monitoring (metrics, alerting)
  - **ASG** (in tandem with CloudWatch) to manage auto-scaling of the EC2 resources
  - **AWS Backups** for the backups, this could be useful who knows

 ***Note 1** : Other AWS services can be used if needed depending on the project needs evolution*<br/>
 ***Note 2** : For this first project, we will limit ourselves to a deployment on a single region with several Availability Zones (AZ)*

*< insert infrastructure schema >*

Regarding the deployment, we have chosen to use Terraform to provision the infrastructure. The Terraform manifests are hosted on this GitHub repository and the `tfstate` will be stored on an internal PostgreSQL database outside of AWS.
