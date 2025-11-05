# Create Amazon EKS Cluster using eksctl (CLI with IAM Role)

#### What is Amazon EKS
- Amazon EKS is a fully managed container orchestration service. EKS allows you to quickly deploy a production ready Kubernetes cluster in AWS, deploy and manage containerized applications more easily with a fully managed Kubernetes service.

<img width="400" height="267" alt="image" src="https://github.com/user-attachments/assets/12d2a106-ead6-4881-a2f4-3592b47c53a6" />

- EKS takes care of master node/control plane. We need to create worker nodes.

#### EKS cluster can be created in following ways:
1. AWS console
2. AWS CLI
3. eksctl command
4. Terraform ( https://github.com/kily-king/Setup-monitoring-EKS-Cluster-Prometheus-Grafana/blob/main/terraform.md )

- We will create EKS cluster using eksctl command line tool.

#### Pre-requisites:
- This Lab is using Jenkins EC2 instance. Jenkins EC2 instance needs to have following configured:
     - Install AWS CLI – Command line tools for working with AWS services, including Amazon EKS.
     - Install eksctl – A command line tool for working with EKS clusters that automates many individual tasks.
     - Install kubectl  – A command line tool for working with Kubernetes clusters.
          - https://github.com/kily-king/Setup-monitoring-EKS-Cluster-Prometheus-Grafana/blob/main/kubectl.md
      
### Create IAM Role with Administrator Access
- You need to create an IAM role with AdministratorAccess policy.
- Go to AWS console, IAM, click on Roles. create a role

<img width="320" height="214" alt="image" src="https://github.com/user-attachments/assets/91450856-2282-4781-b18c-ccc7c7558aa9" />

- Select AWS services, Click EC2, Click on Next permissions.

<img width="320" height="208" alt="image" src="https://github.com/user-attachments/assets/d218ab49-508f-4203-baec-6caf8b7dd2b0" />

- Now search for AdministratorAccess policy and click

<img width="320" height="30" alt="image" src="https://github.com/user-attachments/assets/1e5d7e08-5f5c-4197-816d-1512f6b34907" />

- Skip on create tag. Now give a role name and create it.

<img width="320" height="218" alt="image" src="https://github.com/user-attachments/assets/ed3719cc-2e61-456b-b612-f910f3047df4" />

#### Assign the role to EC2 instance
- Go to AWS console, click on EC2, select EC2 instance, Choose Security.
     - Click on Modify IAM Role

<img width="320" height="204" alt="image" src="https://github.com/user-attachments/assets/b24b41ac-ee80-4efd-a710-7dca3cecb9e7" />

     - Choose the role you have created from the dropdown. Select the role and click on Apply.

<img width="320" height="250" alt="image" src="https://github.com/user-attachments/assets/6d43c602-933c-4f35-9e33-1ab2defd81b0" />

<img width="200" height="98" alt="image" src="https://github.com/user-attachments/assets/cbdb194f-ded4-41dd-a8c8-079ed1593e30" />


## Switch to Jenkins user
- sudo su - jenkins



- 










