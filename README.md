# Ansible Role: ansible-provi_proxmox_kvm

## Description

[![Build Status](https://travis-ci.com/lotusnoir/ansible-provi_proxmox_kvm.svg?branch=master?style=flat)](https://travis-ci.com/lotusnoir/ansible-provi_proxmox_kvm)
[![License](https://img.shields.io/badge/license-Apache--2.0-brightgreen?style=flat)](https://opensource.org/licenses/Apache-2.0)
[![Ansible Role](https://img.shields.io/badge/galaxy-provi_proxmox_kvm-purple?style=flat)](https://galaxy.ansible.com/lotusnoir/provi_proxmox_kvm)
![GitHub repo size](https://img.shields.io/github/repo-size/lotusnoir/ansible-provi_proxmox_kvm?color=orange&style=flat)
![Ansible Quality Score](https://img.shields.io/ansible/quality/52300)
[![downloads](https://img.shields.io/ansible/role/d/52300)](https://galaxy.ansible.com/lotusnoir/provi_proxmox_kvm)
[![Version](https://img.shields.io/github/release/lotusnoir/ansible-provi_proxmox_kvm.svg)](https://github.com/lotusnoir/ansible-provi_proxmox_kvm/releases/)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-provi_proxmox_kvm&metric=alert_status)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-provi_proxmox_kvm)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-provi_proxmox_kvm&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-provi_proxmox_kvm)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-provi_proxmox_kvm&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-provi_proxmox_kvm)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-provi_proxmox_kvm&metric=security_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-provi_proxmox_kvm)

Provisioning and modify [proxmox_vms](https://www.proxmox.com/en/) from clone template.

## Role variables

| Name                    | Default Value  | Description                        |
| ----------------------- | -------------- | -----------------------------------|
| `proxmox_api_user`      | ansible@pve    | pve admin user |
| `proxmox_api_pass`      | pve-admin-pass | pve admin pass |
| `proxmox_api_host`      | proxmox-01     | api host name |
| `proxmox_api_port`      | 8006           | api host port |
| `proxmox_api_scheme`    | https          | api host scheme |
| `proxmox_template`      | debian-buster  | name of template vm to clone |
| `proxmox_template_node` | proxmox-node-1 | node where is located the template vm to clone|
| `proxmox_vm_storage`    | localvm        | storage where to store the clone vm |
| `proxmox_vm_format`     | qcow2          | formet of the clone vm |
| `debug_exec`            | false          | activate ansible debug trace in case of problems |


## Proxmox Template creation steps

1/ add iso file on proxmox
node > storage > content > upload
2/ create vm from image
3/ install OS + packages cloud-init and qemu-guest-agent
4/ Select vm > hardware > add > cloudinit drive
5/ Select vm > options > qemu agent > activate both boxes
6/ Select vm > right click > convert image to template

## Role steps

- Set facts from vm_configuration
- Create tickets for api calls
- check if vm already exists
  - no > create vm
  - yes > get vmid and node infos
- Compare vm_configuration and vm on proxmox
     - true > apply values on vm_configuration
     - false > skip


## Playbook examples

	---
	- hosts: testvm
      connection: local
	  gather_facts: yes
	  roles:
	    - role: ansible-provi_proxmox_kvm
      vars:
        vm_configuration:
          - ip: '10.10.10.10'
            subnet: "3508"
            cluster: "localisation"
            node: "proxmox-node-3"
            memory: 2048
            sockets: 1
            cores: 1
            disk_size_GB: 10

## License

This project is licensed under Apache License. See [LICENSE](/LICENSE) for more details.
