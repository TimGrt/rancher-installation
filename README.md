# Rancher Deployment
Ansible Playbook to deploy Rancher on a Kubernetes cluster.  

[![Ansible Lint](https://github.com/TimGrt/rancher-installation/actions/workflows/ci.yml/badge.svg)](https://github.com/TimGrt/rancher-installation/actions/workflows/ci.yml) [![CodeFactor](https://www.codefactor.io/repository/github/timgrt/rancher-installation/badge?s=8a1fa57a97b376d5cc8d594f9b3178b63a9fd796)](https://www.codefactor.io/repository/github/timgrt/rancher-installation)

The playbook installs Helm on the Ansible Master node, appropriate sudo permissions must be available. The Rancher deployment needs certificates, cert-manager is therefor installed on the Kubernetes cluster by the playbook. Necessary kube config is read from the Kubernetes master node.  
The Rancher `stable` release is installed by default, to install the `latest` release, change the default variable in the `rancher` role.  
Tested with self-hosted k3s cluster on Raspberry Pi's, but should also work with other Kubernetes distributions. The Master node was x86 with Ubuntu.

## Requirements
Minimum Ansible requirements:

ansible-base (2.10.0 or higher)

**or**

ansible-core (2.11.0 or higher)

The following Ansible Collections are necessary:
* ansible.posix
* community.general
* community.kubernetes

Missing collections can be installed with the provided `requirements.yml` file.
```bash
ansible-galaxy collection install -r requirements.yml
```

The following Python packages are necessary:
* openshift
* yaml

Missing collections can be installed with the provided `requirements.yml` file.
```bash
pip3 install -r requirements.txt
```

The playbook expects a running Kubernetes cluster, at least the Kubernetes master node must be reachable to get the kube config file, all tasks are then executed on localhost.

## Execution

Execute the playbook:
```bash
ansible-playbook -i hosts main.yml
```

## Author
Created 2021 by Tim Grützmacher
