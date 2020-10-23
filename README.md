ansible-role-v2ray
==================

[![Ansible Role: bit_kitchen.v2ray](https://img.shields.io/ansible/role/51339.svg)](https://galaxy.ansible.com/bit_kitchen/v2ray)
[![Build Status: bit-kitchen/ansible-role-v2ray](https://travis-ci.org/bit-kitchen/ansible-role-v2ray.svg?branch=master)](https://travis-ci.org/bit-kitchen/ansible-role-v2ray)

```sh
ansible-galaxy install bit_kitchen.v2ray
```

An Ansible role that installs V2Ray on Arch Linux or OpenWrt, and optionally copies V2Ray config file.

Requirements
------------

None.

Role Variables
--------------

Variable            | Default   | Comment
------------------- | --------- | -------
v2ray_latest        | yes       | Whether to upgrade V2Ray if already installed
v2ray_config        | undefined | V2Ray config file to copy to remote machine
v2ray_config_target | Arch Linux: `/etc/v2ray/config.json` <br> OpenWrt: `/etc/config/v2ray` | V2Ray config path on remote machine
**OpenWrt Specific variables**  |
luci                | yes       | Whether to add luci support
minimal             | no        | `yes` for *v2ray-core-mini*, `no` for *v2ray-core*

Dependencies
------------

* `gekmihesg.openwrt` for OpenWrt support

Example Playbook
----------------

### Arch Linux

```yml
- name: Install V2Ray only
  hosts: localhost
  gather_facts: yes
  roles:
    - role: bit_kitchen.v2ray
```

```yml
- name: Install and Configure V2Ray
  hosts: localhost
  gather_facts: yes
  roles:
    - role: bit_kitchen.v2ray
      v2ray_config: ./v2ray-config.json
```

### OpenWrt

```yml
- name: Install V2Ray only
  hosts: openwrt
  remote_user: root
  gather_facts: yes
  roles:
    - role: bit_kitchen.v2ray
      luci: yes     # Whether to add luci support
      minimal: no   # Yes for v2ray-core-mini, no for v2ray-core
```

```yml
- name: Install and Configure V2Ray
  hosts: openwrt
  remote_user: root
  gather_facts: yes
  roles:
    - role: bit_kitchen.v2ray
      luci: yes     # Whether to add luci support
      minimal: no   # Yes for v2ray-core-mini, no for v2ray-core
      v2ray_config: ./v2ray
```

License
-------

[MIT](LICENSE)

Author Information
------------------

[bit.kitchen](https://github.com/bit-kitchen)
