Role Name
=========

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Provision a new VPS server with hardened [SSH](https://www.ssh.com/ssh/), [FW](https://netfilter.org/), [Fail2Ban](https://www.fail2ban.org).

Requirements
------------

Python passlib to generate password

Role Variables
--------------

- `username:` 
- `password:` 
- `public_key:` 

Dependencies
------------

None.

Example Playbook
----------------

```YAML
---
- name: Provision a new VPS server with hardened SSH,FW,Fail2Ban.

  hosts: all
  remote_user: root
  # become: true

  vars:
    username: vagrant

    # To generate password You need python passlib
    # pip install passlib
    # python -c 'from passlib.hash import sha512_crypt; print sha512_crypt.encrypt("password")'

    password: $6$rounds=656000$ukFInLfYjnU47KV8$ILsHAEZwNLG2LXHZ/Pq4YgrpPWKyTfsoMWcOh5OXC2hlaMDGg9j7bRGtE/MAperRJWMpYTeCe7g.wF/M8EhIU.
    public_key: ~/.ssh/id_rsa.pub

  roles:
    - user
    - packages
    - ssh
    - iptables
    - fail2ban

```
