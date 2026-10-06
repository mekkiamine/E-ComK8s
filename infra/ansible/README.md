# E-ComK8s Ansible Infrastructure

This directory contains the Ansible automation used to prepare and bootstrap
the Kubernetes infrastructure for the E-ComBricoM project.

## Architecture

- 1 Kubernetes control plane
- 2 Kubernetes workers
- Ubuntu 24.04
- containerd
- kubeadm
- kubelet
- kubectl
- Flannel CNI

## Node Inventory

| Node    | IP            | Role          |
|---------|---------------|---------------|
| master  | 192.168.0.240 | Control plane |
| worker1 | 192.168.0.6   | Worker        |
| worker2 | 192.168.0.223 | Worker        |

## Automation Roles

### common
Prepares the operating system:
- timezone
- required packages
- swap disabling
- kernel modules
- Kubernetes sysctl settings
- chrony

### containerd
Installs and configures:
- containerd
- Docker repository
- CRI configuration
- crictl
- systemd cgroups

### kubernetes
Installs:
- kubeadm
- kubelet
- kubectl

and configures the Kubernetes package repository and kubelet.

### cluster
Automates:
- kubeadm initialization
- kubeconfig setup
- Flannel installation
- worker joining
- cluster verification

## Execution

From this directory:

```bash
cd /home/k8s-siga/E-ComK8s/infra/ansible

ansible-inventory --graph
ansible-playbook playbooks/site.yml
### cluster
Automates:
- kubeadm initialization
- kubeconfig setup
- Flannel installation
- worker joining
- cluster verification

## Execution

From this directory:

```bash
cd /home/k8s-siga/E-ComK8s/infra/ansible

ansible-inventory --graph
ansible-playbook playbooks/site.yml
