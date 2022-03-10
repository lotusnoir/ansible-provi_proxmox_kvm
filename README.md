# ansible-provi_proxmox_kvm

## Description

[![Galaxy Role](https://img.shields.io/badge/galaxy-provi_proxmox_kvm-purple?style=flat)](https://galaxy.ansible.com/lotusnoir/provi_proxmox_kvm)
[![Version](https://img.shields.io/github/release/lotusnoir/ansible-provi_proxmox_kvm.svg)](https://github.com/lotusnoir/ansible-provi_proxmox_kvm/releases/latest)
![GitHub repo size](https://img.shields.io/github/repo-size/lotusnoir/ansible-provi_proxmox_kvm?color=orange&style=flat)
[![downloads](https://img.shields.io/ansible/role/d/53224)](https://galaxy.ansible.com/lotusnoir/provi_proxmox_kvm)
![Ansible Quality Score](https://img.shields.io/ansible/quality/53224)
[![License](https://img.shields.io/badge/license-Apache--2.0-brightgreen?style=flat)](https://opensource.org/licenses/Apache-2.0)

Provisioning and modify [proxmox_vms](https://www.proxmox.com/en/) from clone template

## Requirements

none

## Role variables

See [variables](/defaults/main.yml) for more details.

## Proxmox Template creation steps

- add iso file on proxmox
node > storage > content > upload
- create vm from image
- install OS + packages cloud-init and qemu-guest-agent
- Select vm > hardware > add > cloudinit drive
- Select vm > options > qemu agent > activate both boxes
- Select vm > right click > convert image to template

## Role steps

- Set facts from vm_configuration
- Create tickets for api calls
- check if vm already exists
  - no > create vm
  - yes > get vmid and node infos
- Compare vm_configuration and vm on proxmox and set changes vars
     - true > apply values from vm_configuration
     - false > skip

## Examples

        ---
        - hosts: provi_proxmox_kvm
          become: true
          become_method: sudo
          gather_facts: true
          roles:
            - role: ansible-provi_proxmox_kvm
          vars:
            vm_configuration:
              - name: "vmtocreate"
                ip: '10.10.10.10'
                subnet: "3508"
                cluster: "localisation"
                node: "proxmox-node-3"
                memory: 2
                sockets: 1
                cores: 1
                disk_size_GB: 10



## License

This project is licensed under Apache License. See [LICENSE](/LICENSE) for more details.

