Foundry Sytemd Unit
=========

Install Foundry on your server as Systemd Unit with `foundry` user

**Warning**: This role **does not** manipulate with `options.json`, so 

Requirements
------------

1. License to Foundry
2. Timed URL to Linux distribution of Foundry

Role Variables
--------------

Commonly edited variables:
- `foundry_distrib_url` (default: undefined) - timed URL to Linux distribution of your Foundry
- `foudnry_update` (default: `false`) - flag to update Foundry if it is already installed. If false and Foundry is already installed, further steps will be skipped
- `foundry_port` (default: `''`) - port that Foundry will listen to. If empty (`''`), then will user default Foundry port

Comonnly left unchanged variables:
- `foundry_home` - home directory of `foundry` user
- `foundry_service_dir` - directory for unit file
- `foundry_service_name` - name of unit

Dependencies
------------

- [`geerlingguy.nodejs`](https://galaxy.ansible.com/ui/standalone/roles/geerlingguy/nodejs/) - to install NodeJS (Foundry dependency)
- [`andrewrothstein.unarchive-deps`](https://galaxy.ansible.com/ui/standalone/roles/andrewrothstein/unarchive-deps/) - to install archive utilities for `unarchive` Ansible module
A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

To install Foundry once
```yaml
    - hosts: servers
      roles:
         - { role: kinjalik.foundry-systemd, foundry_distrib_url=[DATA EXPLUNGED] }
```

To reinstall existing installation
```yaml
    - hosts: servers
      roles:
         - { role: kinjalik.foundry-systemd, foundry_distrib_url=[DATA EXPLUNGED], foundry_update=true }
```

License
-------

BSD
