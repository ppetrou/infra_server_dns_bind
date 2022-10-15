infra_server_dns_bind
=========

A simple role to install and configure bind.

Requirements
------------

* dnspython (python library, http://www.dnspython.org/) installed in the ansible controller


Role Variables
--------------

```
Variable                              Level                 Description

infra_server_dns_bind_version         Default               Bind Version
infra_server_dns_bind_port            Default               Bind Port
infra_server_dns_bind_server_name     Default               DNS Server Name
infra_server_dns_bind_admin_email     Default               DNS Server Admin Email
infra_server_dns_bind_zones           Default               DNS Zones (Forward and Reverse)
infra_server_dns_bind_ip              Default               Bind Listen IP
infra_server_dns_bind_run_assertions  Default               Flag whether to run dig assertions
```

Dependencies
------------

NA

Example Playbook
----------------

```
---
- hosts: dns_server
  become: yes
  roles:
    - role: infra_server_dns_bind
      vars:
        infra_server_dns_bind_version: 32:9.11.36-3.el8
        infra_server_dns_bind_port: 53
        infra_server_dns_bind_server_name: devserver.local
        infra_server_dns_bind_admin_email: admin.email.com
        infra_server_dns_bind_ip: 192.168.122.55
        infra_server_dns_bind_run_assertions: yes
        infra_server_dns_bind_zones:
          - name: example.local
            reverse_zone: 168.192.in-addr.arpa
            a_records:
              - name: subdomain1
                ip: 192.168.1.111
              - name: subdomain2
                ip: 192.168.1.121
```

License
-------

Apache 2.0

Author Information
------------------

```
Petros Petrou
ppetrou@gmail.com
```
