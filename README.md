Role Name
=========

haproxy

[![Build Status](https://travis-ci.org/cmihai-ansible/haproxy.svg?branch=master)](https://travis-ci.org/cmihai-ansible/haproxy)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.haproxy](https://galaxy.ansible.com/devops-toolbox.haproxy)

```bash
ansible-galaxy install devops-toolbox.haproxy
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.

Role Variables
--------------

```yaml
# defaults file for haproxy

# Service
haproxy_enable_service: true
haproxy_copy_templates: true
haproxy_firewall_configure: true
haproxy_firewall_rules:
  - service: http

# Frontend
haproxy_frontend_port: 80

# Backend
haproxy_backend_name: app
haproxy_backend_port: 80
haproxy_backend_servers:
  - name: web01
    address: 192.168.0.1
  - name: web02
    address: 192.168.0.2
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install haproxy on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: haproxy is configured
      import_role:
        name: devops-toolbox.haproxy
      vars:
        # defaults file for haproxy

        # Service
        haproxy_enable_service: true
        haproxy_copy_templates: true
        haproxy_firewall_configure: true
        haproxy_firewall_rules:
          - service: http

        # Frontend
        haproxy_frontend_port: 80

        # Backend
        haproxy_backend_name: app
        haproxy_backend_port: 80
        haproxy_backend_servers:
          - name: web01
            address: 192.168.0.1
          - name: web02
            address: 192.168.0.2
      tags: haproxy
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
