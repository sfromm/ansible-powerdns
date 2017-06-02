PowerDNS
==========

A role to manage [PowerDNS](https://www.powerdns.com).

Requirements
------------

No external dependencies.

Role Variables
--------------

- **powerdns_setuid**:
- **powerdns_setgid**:
- **powerdns_recursor_setuid**:
- **powerdns_recursor_setgid**:
- **powerdns_backends**:
- **powerdns_use_recursor**:  Whether to deploy PowerDNS standalone
  recursor server.
- **powerdns_use_authoritative**:  Whether to deploy PowerDNS standalone
  authoritative server.
- **powerdns_is_master**:  If an authoritative server, whether this will
  be a master for a zone.
- **powerdns_is_slave**:  If an authoritative server, whether this will
be a slave for a zone.
- **powerdns_local_address**: List of addresses to listen on for
  queries.  Defaults to ```127.0.0.1```.  You are encouraged to consider
  using ```ansible_all_ipv4_addresses``` and
  ```ansible_all_ipv6_addresses```.  One example is:
```
powerdns_local_address: "{{ ansible_all_ipv4_addresses + ansible_all_ipv6_addresses }}"
```

The following are ACL related:

- **powerdns_allow_recursion**: A list of IP ranges to allow recursion
  to.  This defaults to *127.0.0.1*.  This is used when
  **powerdns_use_authoritative** is enabled.
- **poweredns_allow_axfr_ips**: A list of IP ranges to allow AXFR to.
  This defaults to *127.0.0.1*.  This is used when
  **powerdns_use_authoritative** is enabled.

The following are specific to the BIND backend:

- **powerdns_use_bind_backend**
- **powerdns_bind_config**
- **powerdns_bind_directory**
- **powerdns_bind_check_interval**

Dependencies
------------

No dependency on other roles.

Example Playbook
----------------

A trivial example:

    - hosts: servers
      roles:
         - { role: sfromm.powerdns }

License
-------

GPLv2

Author Information
------------------

See https://github.com/sfromm
