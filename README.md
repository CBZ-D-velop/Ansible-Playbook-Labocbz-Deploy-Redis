# Ansible playbook: labocbz.deploy_redis

![Licence Status](https://img.shields.io/badge/licence-MIT-brightgreen)
![CI Status](https://img.shields.io/badge/CI-success-brightgreen)
![Testing Method](https://img.shields.io/badge/Testing%20Method-Ansible%20Molecule-blueviolet)
![Testing Driver](https://img.shields.io/badge/Testing%20Driver-docker-blueviolet)
![Language Status](https://img.shields.io/badge/language-Ansible-red)
![Compagny](https://img.shields.io/badge/Compagny-Labo--CBZ-blue)
![Author](https://img.shields.io/badge/Author-Lord%20Robin%20Crombez-blue)

## Description

![Tag: Ansible](https://img.shields.io/badge/Tech-Ansible-orange)
![Tag: Debian](https://img.shields.io/badge/Tech-Debian-orange)
![Tag: Redis](https://img.shields.io/badge/Tech-Redis-orange)
![Tag: SSL/TLS](https://img.shields.io/badge/Tech-SSL%2FTLS-orange)
![Tag: mTLS](https://img.shields.io/badge/Tech-mTLS-orange)

An Ansible playbook to deploy and configure Redis on your host.

This Ansible playbook streamlines the installation of a standalone Redis service or daemon. It offers the flexibility to provide a list of ports for installing multiple Redis services on those specified ports. This feature is designed to enable the creation of a Redis cluster with just three available servers instead of the standard nine minimum requirement.

With this playbook, you can effortlessly set up Redis to suit your specific needs, whether it's a single Redis instance or a simplified Redis cluster, making it a powerful tool for managing your data caching and storage solutions.

## Deployment diagramm

![](./assets/Ansible-Playbook-Labocbz-Deploy-Redis.drawio.svg)

This is a potential deployment carried out using this playbook. We can observe a Redis service component along with its subsystem. This subsystem consists of nine servers distributed across three hosts. Therefore, a triple-master cluster with six slaves is feasible. Communications are end-to-end encrypted with TLS, and mTLS is possible, although it is currently not well-managed by Redis.

## Tests and simulations

### Basics

You have to run multiples tests. *tests with an # are mandatory*

```MARKDOWN
# lint
# syntax
# converge
# idempotence
# verify
side_effect
```

Executing theses test in this order is called a "scenario" and Molecule can handle them.

Molecule use Ansible and pre configured playbook to create containers, prepare them, converge (run the playbook) and verify its execution.
You can manage multiples scenario with multiples tests in order to get a 100% code coverage.

This playbook contains a ./tests folder. In this folder you can use the inventory or the tower folder to create a simualtion of a real inventory and a real AWX / Tower job execution.

### Command reminder

```SHELL
# Check your YAML syntax
yamllint -c ./.yamllint .

# Check your Ansible syntax and code security
ansible-lint --config=./.ansible-lint .

# Execute and test your playbook
molecule lint
molecule create
molecule list
molecule converge
molecule verify
molecule destroy

# Execute all previous task in one single command
molecule test
```

## Installation

To install this playbook, just copy/import this playbook or raw file into your fresh playbook repository or call it with the "include_playbook/import_playbook" module.

## Usage

### Vars

```YAML
# From inventory
---
# all vars from to put/from your inventory
# see tests/inventory/group_var for all groups and vars.
```

```YAML
# From AWX / Tower
---
all vars from to put/from AWX / Tower
```

## Architectural Decisions Records

Here you can put your change to keep a trace of your work and decisions.

### 2023-10-16: First Init

* First init of this playbook with the bootstrap_playbook playbook by Lord Robin Crombez

### 2023-10-19: Fix and push

* Fix permissions on certs
* Playbook install a Redis standole service
* Playbook can install multiples Redis services and daemon
* Playbook doesn't init the cluster, for now

## Authors

* Lord Robin Crombez

## Sources

* [Ansible playbook documentation](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_playbooks.html)
* [Ansible Molecule documentation](https://molecule.readthedocs.io/)
* [labocbz.install_redis](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Redis.git)
