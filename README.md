# k8s
------------
Ansible scripts to deploy Kubernetes on Ubuntu virtual machines or servers.

## Getting Started

This is an example of how to deploy the Kubernetes cluster to Ubuntu virtual machines or servers.

### Prerequisites

This is an example of how to list things you need to use the Ansible scripts.
* Minimum two virtual machines with Ubuntu
* [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## The Ansible scripts overview

Below you can find the description of the Ansible scripts, files, and roles.

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
└── vaults.yml
  ```
