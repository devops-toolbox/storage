Role Name
=========

storage: Storage

[![Build Status](https://travis-ci.org/cmihai-ansible/storage.svg?branch=master)](https://travis-ci.org/cmihai-ansible/storage)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.storage](https://galaxy.ansible.com/devops-toolbox.storage)

```bash
ansible-galaxy install devops-toolbox.storage
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
storage_packages_state: present
storage_remove_packages: true
storage_enable_service: true
storage_enable_selinux: true
storage_copy_templates: true
storage_firewall_configure: true
storage_firewall_rules:
  - service: ssh
  - port: 3389
storage_users:
  - user: devops
    group: docker
storage_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install storage on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: storage is configured
      import_role:
        name: devops-toolbox.storage
      vars:
        storage_packages_state: present
        storage_remove_packages: true
        storage_enable_service: true
        storage_enable_selinux: true
        storage_copy_templates: true
        storage_firewall_configure: true
        storage_firewall_rules:
          - service: ssh
          - port: 3389
        storage_users:
          - user: devops
            group: docker
        storage_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: storage
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
