# Ansible role: transmission-daemon
[![Build Status](https://travis-ci.org/danielkoster/ansible-role-transmission-daemon.svg?branch=master)](https://travis-ci.org/danielkoster/ansible-role-transmission-daemon)
[![Ansible Role](https://img.shields.io/ansible/role/16042.svg)](https://galaxy.ansible.com/danielkoster/transmission-daemon/)

Installs and configures the Transmission daemon on Debian/Ubuntu servers.

## Requirements
There are no special requirements. Note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

```yaml
- hosts: transmission
  roles:
    - role: danielkoster.transmission-daemon
      become: yes
```

## Role Variables
Every option in the `settings.json` configuration file can be specified. See the [Transmission wiki](https://github.com/transmission/transmission/wiki/Editing-Configuration-Files) for a complete list of configurable options. Note that the variables in this role use underscores and are prefixed with `transmission_`. So if you'd like to override `rpc-enabled` you can do so by defining `transmission_rpc_enabled`. For the default values, see `defaults/main.yml`. Theses are taking from the default configuration file the transmission-daemon package generates.

__NOTE__: Make sure you set `transmission_rpc_password` to a secure password, or disable RPC login.

## Example Playbook
```yaml
- hosts: transmission
  become: yes
  roles:
    - { role: danielkoster.transmission-daemon }
```

*Inside `vars/main.yml`*:
```yaml
transmission_dht_enabled: false
transmission_max_peers_global: 1000
```
