Role Name
=========

Ansible role to install TIG stack, Telegraf, InfluxDB and Grafana in docker containers

Requirements
------------

Docker installed on target machine see Dependencies

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.


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
  hosts: [tig_combined]
  gather_facts: true
  become: yes
  vars:
    show_debug: true
    tig_distributed: false
  environment:
    PYTHONPATH: "/home/<YOUR USERNAME>/.local/lib/python3.7/site-packages/"
  tasks:
    - name: Include role for TIG stack
      include_role:
        name: tig_stack_docker

EDIT the: <YOUR USERNAME> with your ownd account logging in to the tig-stack server


License
-------

BSD

Author Information
------------------

Created by Bart Smeding bartsmeding@yaworks.com / mail@bartsmeding.nl / https://github.com/bsmeding
