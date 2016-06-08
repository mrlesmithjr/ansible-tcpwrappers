Role Name
=========

An Ansible role to manage TCP Wrappers..

Requirements
------------

None

Role Variables
--------------

````
---
# defaults file for ansible-tcpwrappers
# Wildcards can be used
  # ALL - Matches everything.
  # LOCAL - Matches hostnames that don’t contain a dot (.).
  # UNKNOWN - Matches any user/hostname whose name is not known.
  # KNOWN - Matches any user/hostname whose name is known.
  # PARANOID - Matches any host whose name doesn’t match its address

tcpwrappers_allow:
  - daemon: 'sshd'
    clients:
      - 'ALL'
#      - '10.0.0.0/8'
#      - '172.16.0.0/16'
#      - '192.168.0.0/16'
  - daemon: 'ALL'
    clients:
      - 'localhost'
tcpwrappers_allow_all_connections: false  #Defines if all connections are allowed
tcpwrappers_deny:
  - daemon: 'sshd'
    clients:
      - '202.54.1.20'
      - '64.66.44.22'
      - '64.66.44.25'
tcpwrappers_deny_all_connections: true  #Defines if all connections are denied
````

Dependencies
------------

None

Example Playbook
----------------

````
---
- hosts: all
  become: true
  vars:
  roles:
    - role: ansible-tcpwrappers
  tasks:
````

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
