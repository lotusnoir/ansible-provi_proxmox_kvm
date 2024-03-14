# ansible-provi_proxmox_kvm

[![Galaxy Role](https://img.shields.io/badge/galaxy-provi_proxmox_kvm-purple?style=flat)](https://galaxy.ansible.com/lotusnoir/provi_proxmox_kvm)
[![Version](https://img.shields.io/github/release/lotusnoir/ansible-provi_proxmox_kvm.svg)](https://github.com/lotusnoir/ansible-provi_proxmox_kvm/releases/latest)
[![GitHub repo size](https://img.shields.io/github/repo-size/lotusnoir/ansible-provi_proxmox_kvm?color=orange&style=flat)](https://galaxy.ansible.com/lotusnoir/provi_proxmox_kvm)
[![downloads](https://img.shields.io/ansible/role/d/53224)](https://galaxy.ansible.com/lotusnoir/provi_proxmox_kvm)
[![Ansible Quality Score](https://img.shields.io/ansible/quality/53224)](https://galaxy.ansible.com/lotusnoir/provi_proxmox_kvm)
[![License](https://img.shields.io/badge/license-Apache--2.0-brightgreen?style=flat)](https://opensource.org/licenses/Apache-2.0)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Description](#description)
- [Requirements](#requirements)
- [Role variables](#role-variables)
- [Examples](#examples)
- [License](#license)
- [Author Information](#author-information)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Description

Provisioning and modify [proxmox_vms](https://www.proxmox.com/en/) from clone template
## Requirements

none

## Role variables

See [variables](/defaults/main.yml) for more details.

## Examples

        ---
        - hosts: provi_proxmox_kvm
          become: true
          become_method: sudo
          gather_facts: true
          roles:
            - role: ansible-provi_proxmox_kvm


## License

This project is licensed under Apache License. See [LICENSE](/LICENSE) for more details.

## Author Information

- [Philippe LEAL](https://github.com/lotusnoir)
