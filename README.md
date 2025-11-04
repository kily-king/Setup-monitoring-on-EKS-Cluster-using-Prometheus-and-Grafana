# Setup-monitoring-on-EKS-Cluster-using-Prometheus-and-Grafana

<img width="400" height="225" alt="image" src="https://github.com/user-attachments/assets/ad9d8b24-7422-4fe2-acc5-3934d725210a" />

#### What is Prometheus?
- Note
     - Prometheus is an open source monitoring tool
     - Provides out-of-the-box monitoring capabilities for the Kubernetes container orchestration platform. It can monitor servers and databases as well.
     - Collects and stores metrics as time-series data, recording information with a timestamp 
     - It is based on pull and collects metrics from targets by scraping metrics HTTP endpoints.

#### What is Grafana?
- Note
     - Grafana is an open source visualization and analytics software. 
     - It allows you to query, visualize, alert on, and explore your metrics no matter where they are stored.
#### Why System monitoring is critical?
- Note
     - **Alerting**: can give early warning of issues or problems before they become serious, costly or irreversible.
     - **Visibility**: Monitoring provides real-time insights into the health and performance of your applications and infrastructure.
     - **Capacity Planning:** By collecting and analyzing data over time, you can make informed decisions about capacity planning, such as when to add or remove nodes, allocate more resources, or scale your applications.

## Prometheus Architecture

<img width="400" height="225" alt="image" src="https://github.com/user-attachments/assets/0a60b377-8d5e-43d6-b92f-39cef54e35b7" />

### Key components:
- Note
     1. Prometheus server - Processes and stores metrics data
     2. Alert Manager - Sends alerts to any systems/channels
     3. Grafana - Visualize scraped data in UI

### Installation Method:
- The are are many ways you can setup Prometheus and Grafana. You can install in following ways:
     1. Create all configuration files of both Prometheus and Grafana and execute them in right order.
     2. Prometheus Operator - to simplify and automate the configuration and management of the Prometheus monitoring stack running on a Kubernetes cluster
     3. Helm chart (Recommended) - Using helm to install Prometheus Operator including Grafana

### Why to use Helm?
- Helm is a package manager for Kubernetes. Helm simplifies the installation of all components in one command. Install using Helm is recommended as you will not be missing any configuration steps and very efficient. 

### Pre-requisites:
- Note
     1. EKS Cluster needs to be up and running. Setup EKS cluster in AWS cloud.
     2. Install Helm3
     3. EC2 instance to access EKS cluster

# Create Amazon EKS cluster by eksctl | How to create EKS cluster in AWS cloud using eksctl | Create EKS Cluster in command line using IAM Role

#### What is Amazon EKS
- Amazon EKS is a fully managed container orchestration service. EKS allows you to quickly deploy a production ready Kubernetes cluster in AWS, deploy and manage containerized applications more easily with a fully managed Kubernetes service.

<img width="400" height="267" alt="image" src="https://github.com/user-attachments/assets/12d2a106-ead6-4881-a2f4-3592b47c53a6" />

- EKS takes care of master node/control plane. We need to create worker nodes.

#### EKS cluster can be created in following ways:
1. AWS console
2. AWS CLI
3. eksctl command
4. Terraform ( https://github.com/kily-king/Setup-monitoring-on-EKS-Cluster-using-Prometheus-and-Grafana/blob/main/terraform.md )



