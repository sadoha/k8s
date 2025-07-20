# k8s
------------
_Ansible scripts to deploy Kubernetes on Ubuntu virtual machines or servers._

## Getting Started

_This is an example of how to deploy the Kubernetes cluster to Ubuntu virtual machines or servers._

### Prerequisites

This is an example of how to list things you need to use the Ansible scripts.
* Minimum two virtual machines with Ubuntu
* [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## The Ansible scripts overview

_Below you can find the description of the Ansible scripts, files, and roles._

#### The layout of directories

  ```sh
├── ansible.cfg
├── common
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── README.md
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   └── vars
│       └── main.yml
├── common.yml
├── control-planes
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── README.md
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   └── vars
│       └── main.yml
├── control-planes.yml
├── inventory.yml
├── LICENSE
├── main.yml
├── README.md
└── vaults.yml  <--- This file should be created manually because this file has sensitive variables.
  ```
### Installation

_Below is an example of how you can set up the Kubernetes cluster on your virtual machines._ 

1. First of all, you should create the **[ vaults.yml ]** file in the root directory with Ansible scripts.
   Create a file with the following content:
   ```sh
   ---
   # The list of hidden credentials or sensitive variables
   ansible_user: loginUserName
   ansible_password: loginPassword
   ansible_become_password: sudoPassword
   ```
