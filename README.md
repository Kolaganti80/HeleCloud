# HeleCloud

About The Project
This project is built to host a PHP application in AWS EC2 instance.

Built With
The project is built using,

AWS resources
Terraform
Ansible
Getting Started
Prerequisites
Create a free tier AWS account.
Create an IAM user with programmable access and make a note of the access and secret keys.
Installation
Clone the repo
Use the repo
Install Terraform
Install Ansible
Usage
Hosting this application involves three steps.

1: Standing up the Infrastructure
The infrastructure is setup in AWS using Terraform.

cd into the infrastructure folder in the cloned repository.
Run the following commands in order
terraform init
terraform plan
terraform apply
This will provision the required infrastructure and provides the EC2 instance public IP as the output.

2: Installing the application
The next step is to install the required softwares in the EC2 instance and deploy the php application along with the MySQL database. This is done using ansible.

Open the inventory.yml file under ansible directory and replace 0.0.0.0 with the public IP copied at the end of part 1.
Replace the contents of the ./ansible/secrets/ssh.private with your private key. This is the private key corresponding to the public key used in Part 1 while provisioning the infrastructure using terraform.
Run the ansible playbook using the below command
ansible-playbook -i inventory.yml application.yml
3: Tear down the application
Run the below command to tear down the application.

- terrafrom destroy
