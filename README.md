# e-commerce-website-deployment

The CTO asked you to deploy an e-commerce system in the AWS cloud in less than 2hrs. The mission aims to determine if the viable product can be used to serve the company products. This is in line with the company’s cost savings initiatives.

Due to limited time, the deployment will do via automation.

•	We will deploy EC2 instances using Terraform.

•	Use Ansible to automate supporting apps provisioning on the EC2 instance. 

## Tool Stack

•	Magento -open source the support e-commerce

•	PHP

•	MySQL

•	Redis – to cache data for easy accessibility by customers



## Part 1

E-commerce MVP deployment

- Create Magento free account on:

  https://marketplace.magento.com/ 

- Create and Save the Public and Private Key from your Magento account.

- Open AWS Cloud Shell

- Install Terraform on AWS Cloud Shell

>sudo yum install -y yum-utils

>sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo

>sudo yum -y install terraform

- Download the Terraform files on AWS Cloud Shell
  
>mkdir final_project

>cd final_project

>wget https://tcb-bootcamps.s3.amazonaws.com/bootcamp-aws/en/final-project-terraform.zip

>unzip final-project-terraform.zip

- Edit Terraform files | variable (same steps done in module 5):

- main.tf:
  
* variables

- Running Terraform to deploy the EC2 VM:

>cd terraform

>terraform init

>terraform plan

>terraform apply

## Part 2

- Connect to your EC2 instance via SSH

- Install Ansible in the EC2 VM

>sudo yum-config-manager --enable epel

>sudo yum install ansible -y

- Download the Ansible playbooks
  
>wget https://tcb-bootcamps.s3.amazonaws.com/bootcamp-aws/en/final-project-ansible-magento2.zip

>unzip final-project-ansible-magento2.zip

- Edit and save Ansible file parameters
  
>cd ansible-magento2

File: group_vars/all.yml

* magento_domain
  
* server_hostname
  
* repo_api_key
  
* repo_secret_key

- Run Ansible to deploy the stack of tools for the e-commerce

>cd ..

>ansible-playbook -i hosts.yml ansible-magento2.yml -k -vvv --become

- Testing the E-commerce website:

Just copy and paste the EC2 Public IP in the browser.

 *in some cases, it can take some minutes to get the website available!

- Setting up the e-commerce:
  
  http://<EC2_PUBLIC_IP>/securelocation

User: Admin

Password: Strong123Password#

(User and Password of the Magento Admin available in the file: group_vars/all.yml)

- Download the ecommerce images and personalize the ecommerce website.
  
 https://tcb-bootcamps.s3.amazonaws.com/bootcamp-aws/en/final-project-images.zip 

-- Content > Configuration > HTML Head > Edit (Default Store View)

--- Default page title: The Clodu Bootcamp Store

--- Header > Logo image: The Cloud Bootcamp logo from images

--- Header > Welcome text: Welcome to The Cloud Bootcamp Store!

--- Cache Refresh (Flush it)

-- Catalog > Products > Add product > The Cloud Bootcamp T-Shirt

--- Price: 80

--- Quantity: 100

--- Images And Videos > Add images

--- Save

-- Content > Pages > Edit Home Pages

--- Click Content > Erase content

--- Insert Widget > Widget type: Catalog New Products List > Insert Widget

--- Check if the customization is in place

- Remove the resources deployed via AWS Cloud Shell

(If needed, re-install the Terraform following the same steps used previously)

>cd ~/final_project/terraform
>terraform destroy



Links:
>Ansible Documentation: https://docs.ansible.com/ansible-core/devel/user_guide/index.html 
