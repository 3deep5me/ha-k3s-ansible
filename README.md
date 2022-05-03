# Build a HA-Kubernetes cluster with load balancing and enhanced security using k3s via Ansible
Ansible Playbooks for K3s cluster with OpenELB as load balancer engine and wireguard for node to node encryption via Ansible.


## current information
you need to wait up to 10 minutes until the cluster is ready
check this out for lb and stuff:
https://www.youtube.com/watch?v=9PLw1xalcYA

## ToDo
- [ ] Add OpenELB
- [ ] Add wireguard for node to node encryption
- [ ] configure (continuous) testing

## System requirements

Deployment environment must have Ansible 2.4.0+
Master and nodes must have passwordless SSH access

## Usage

First create a new directory based on the `sample` directory within the `inventory` directory:

```bash
cp -R inventory/sample inventory/my-cluster
```

Second, edit `inventory/my-cluster/hosts.ini` to match the system information gathered above. For example:

```bash
[master]
192.16.35.[12:14]

[node]
192.16.35.[15:17]

[k3s_cluster:children]
master
node
```

You probably need to edit `inventory/my-cluster/group_vars/all.yml` to match your environment.

Start provisioning of the cluster using the following command:

```bash
ansible-playbook site.yml -i inventory/my-cluster/hosts.ini
```

## Kubeconfig

To get access to your **Kubernetes** cluster just

```bash
scp debian@master_ip:~/.kube/config ~/.kube/config
```


## K3s Ansible Playbook

Build a Kubernetes cluster using Ansible with k3s. The goal is easily install a Kubernetes cluster on machines running:

- [ ] Debian
- [ ] Ubuntu
- [ ] Rocky Linux

on processor architecture:

- [ ] x64
- [ ] arm64
- [ ] armhf

