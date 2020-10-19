ansible-role-v2ray
==================

An Ansible role that installs V2Ray on Arch Linux or OpenWrt.

Requirements
------------

None.

Role Variables
--------------

### OpenWrt Specific variables

Variable   | Default | Comment
---------- | ------- | -------
luci       | yes     | Whether to add luci support
minimal    | no      | `yes` for *v2ray-core-mini*, `no` for *v2ray-core*

Dependencies
------------

* `gekmihesg.openwrt` for OpenWrt support

Example Playbook
----------------

### Arch Linux

```yml
- hosts: localhost
  gather_facts: yes
  roles:
    - role: bit_kitchen.v2ray
```

### OpenWrt

```yml
- hosts: openwrt
  remote_user: root
  gather_facts: yes
  roles:
    - role: bit_kitchen.v2ray
      luci: yes     # Whether to add luci support
      minimal: no   # Yes for v2ray-core-mini, no for v2ray-core
```

License
-------

[MIT](LICENSE)

Author Information
------------------

[bit.kitchen](https://github.com/bit-kitchen)
