Role Name
=========

Ansible role to install TIG stack, Telegraf, InfluxDB and Grafana in docker containers

Requirements
------------

Docker installed on target machine see Dependencies

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.


PLEASE NOTE: there are use settings as login names and password, please use host_vars or group_vars for override and encrypt these variable files with ansible-vault


MIBs
----
With Telegraf there are several SNMP mibs shipped (see Docker used default: )
If you need extra / custom mibs place theme on /usr/share/mibs/netsnmp on the target host running the Telegraf container (only working with local_mounts version)


Dependencies
------------

ansible-galaxy install geerlingguy.docker geerlingguy.pip

'''
---
- hosts: [tig_stack]
  vars:
    pip_package: python3-pip
    pip_install_packages:
      - name: docker
      - name: influxdb
    docker_users:
      - <YOUR USERNAME>
  roles:
  roles:
    - name: geerlingguy.pip
    - name: geerlingguy.docker
      become: true
'''
EDIT the: <YOUR USERNAME> with your ownd account logging in to the tig-stack server


Example Playbook
----------------

Install TIG stack role: ansible-galaxy install bsmeding.tig_stack_docker

---
- name: Install TIG stack
  hosts: localhost
  gather_facts: true
  become: yes
  vars:
    show_debug: true
    tig_distributed: false
    influx_reinitialize_database: true
  tasks:
    - name: Include role for TIG stack
      include_role:
        name: bsmeding.tig_stack_docker

EDIT the: <YOUR USERNAME> with your ownd account logging in to the tig-stack server

If you have problems after multiple play runs and changes in docker, please try to restart the docker service on the target

License
-------

BSD

Author Information
------------------

Created by Bart Smeding bartsmeding@yaworks.com / mail@bartsmeding.nl / https://github.com/bsmeding
