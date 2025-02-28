# Automated Kubernetes Application Deployment

## Overview
This project demonstrates my implementation of fully automated Kubernetes deployments using infrastructure-as-code and configuration management tools. I successfully created an AWS EKS cluster with Terraform and deployed applications to it in a streamlined, repeatable manner with Ansible.

## Technologies Used
- **Infrastructure**: Terraform, AWS EKS
- **Configuration Management**: Ansible
- **Orchestration**: Kubernetes
- **Environment**: Linux

## Implementation Details

### Infrastructure Provisioning
I used Terraform to create and manage the AWS EKS cluster, defining all infrastructure components as code. This approach ensures consistency and enables easy replication across different environments.

![Terraform Plan Output Screenshot] <!-- Include screenshot of terraform plan/apply output -->

### Kubernetes Deployment Automation
With the infrastructure in place, I wrote Ansible playbooks to:
- Create a dedicated namespace in the Kubernetes cluster
- Deploy application components to this namespace
- Configure necessary Kubernetes resources (deployments, services, etc.)

![Ansible Playbook Execution] <!-- Include screenshot of ansible playbook running -->

### Deployment Verification
I verified the successful deployment using kubectl commands to inspect the running resources within the newly created namespace.

![Kubernetes Resources Running] <!-- Include screenshot of kubectl get all output showing pods/services -->

## Architecture Diagram
<!-- Include a simple diagram showing the workflow: Terraform → AWS EKS → Ansible → Deployed App -->

## Key Achievements
- Fully automated EKS cluster creation with Terraform
- Isolated application deployment in dedicated namespace
- Repeatable deployment process through Ansible playbooks
- End-to-end automation of cloud infrastructure and application deployment

## Future Enhancements
- Implement CI/CD pipeline integration
- Add monitoring and logging solutions
- Create multi-environment support (dev, staging, prod)

## Conclusion
This project demonstrates my ability to implement modern DevOps practices by automating infrastructure provisioning and application deployment using industry-standard tools.