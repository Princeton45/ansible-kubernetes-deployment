# Automated Kubernetes Application Deployment

## Overview
This project demonstrates my implementation of fully automated Kubernetes deployments using infrastructure-as-code and configuration management tools. I successfully created an AWS EKS cluster with Terraform and deployed applications to it in a streamlined, repeatable manner with Ansible.

![diagram](https://github.com/Princeton45/ansible-kubernetes-deployment/blob/main/images/diagram.png)

## Technologies Used
- **Infrastructure**: Terraform, AWS EKS
- **Configuration Management**: Ansible
- **Orchestration**: Kubernetes
- **Environment**: Linux

## Implementation Details

### Infrastructure Provisioning
I used Terraform to create and manage the AWS EKS cluster, defining all infrastructure components as code. This approach ensures consistency and enables easy replication across different environments.

![terraform](https://github.com/Princeton45/ansible-kubernetes-deployment/blob/main/images/terraform.png)

### Kubernetes Deployment Automation
With the infrastructure in place, I wrote Ansible playbooks to:
- Create a dedicated namespace in the Kubernetes cluster called `testing-my-app`
- Deploy application components to this namespace
- Configure necessary Kubernetes resources (deployments, services, etc.)

Note: I needed to export the kubeconfig file from AWS and place it in `/home/princeton/ansible-playbooks/kubeconfig-myapp` so Ansible can authenticate to the cluster with it.

`deploy-to-k8s.yaml`
```yaml
---
- name: Deploy app in new Namespace
  hosts: localhost
  tasks:
    - name: Create a k8s namespace
      kubernetes.core.k8s:
        name: testing-my-app
        api_version: v1
        kind: Namespace
        state: present
        kubeconfig: /home/princeton/ansible-playbooks/kubeconfig-myapp
    - name: Deploy nginx app 
      kubernetes.core.k8s:
        src: /home/princeton/ansible-playbooks/nginx-config.yaml
        state: present
        kubeconfig: /home/princeton/ansible-playbooks/kubeconfig-myapp
        namespace: testing-my-app

```
![success1](https://github.com/Princeton45/ansible-kubernetes-deployment/blob/main/images/success1.png)

![nginx-success](https://github.com/Princeton45/ansible-kubernetes-deployment/blob/main/images/nginx-success.png)




