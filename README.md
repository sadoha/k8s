# k8s
![screenshot](images/kubernetes-logo.png)
------------
_Ansible scripts to deploy Kubernetes on Ubuntu virtual machines or servers._

## Getting Started

_This is an example of how to deploy the Kubernetes cluster to Ubuntu virtual machines or servers._

### Prerequisites

This is an example of how to list things you need to use the Ansible scripts.
* Minimum two virtual machines with Ubuntu, but the current scripts are for one control-plane node and two workers. 
* [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## The Ansible scripts overview

_Below you can find the description of the Ansible scripts, files, and roles._

#### The layout of directories

  ```sh
├── ansible.cfg
├── common
│   ├── handlers
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   └── vars
│       └── main.yml
├── common.yml
├── control-plane
│   ├── handlers
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   └── vars
│       └── main.yml
├── control-plane.yml
├── images
│   ├── initialize-kubernetes-cluster.png
│   └── kubernetes-logo.png
├── inventory.yml
├── LICENSE
├── main.yml
├── README.md
├── vaults.yml <----------------- This file should be created manually because this file has sensitive variables
├── workers
│   ├── control-plane.yml
│   ├── handlers
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   └── vars
│       └── main.yml
└── workers.yml
  ```
### Installation

_Below is an example of how you can set up the Kubernetes cluster on your virtual machines._ 

1. First of all, you should create the _vaults.yml_ file in the root directory with Ansible scripts.
   Create a file with the following content:
   ```sh
   ---
   # The list of hidden credentials or sensitive variables
   ansible_user: loginUserName
   ansible_password: loginPassword
   ansible_become_password: sudoPassword
   ```
2. In the second step, you have to update the _inventory.yml_ file and update IP addresses for the control-plane, workers, and hostnames.
   ```sh
   control-plane:
      hosts:
        control-plane-01:
          ansible_host: 192.168.0.1                <--- update it
          ansible_host_name: k8s-control-plane-01  <--- update it

    workers:
      hosts:
        worker-01:
          ansible_host: 192.168.0.2                <--- update it
          ansible_host_name: k8s-worker-01         <--- update it
        worker-02:
          ansible_host: 192.168.0.3                <--- update it
          ansible_host_name: k8s-worker-02         <--- update it
   ```
3. In a third step, you can find out how to deploy the Ansible playbooks.

   * _Full deploy, for the control-plane and join all workers._
   ```sh
   ansible-playbook main.yml
   ```

   
## Additional options 

   * _Use the command below if you only need to prepare the control-plane and all workers, without kubeadm init._
   ```sh
   ansible-playbook main.yml --tags common
   ```

   * _Use it if you only need to kubeadm init the control-plane._
   ```sh
   ansible-playbook main.yml --tags control-plane
   ```

   * _Use the command below if you need to prepare the control-plane, all workers, and set up CNI without kubeadm init._
   ```sh
   ansible-playbook main.yml --skip-tags kubeadm-init
   ```
   * _Using this step, you can join any number of worker nodes to the cluster. When the Kubernetes control-plane is initialized successfully in a previous step, you can join any number of worker nodes by running the following._
     
   ```sh
   ansible-playbook main.yml --tags workers
   ```
   * _Also, you can manually join any number of worker nodes._

   ![screenshot](images/initialize-kubernetes-cluster.png)
