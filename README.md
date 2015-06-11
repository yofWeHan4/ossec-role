Role Name
=========

Ansible role to install OSSEC

[![Build Status](https://travis-ci.org/valentinogagliardi/ossec-role.svg?branch=master)](https://travis-ci.org/valentinogagliardi/ossec-role)

Requirements
------------

A compiler must be present on the node machine in order to compile OSSEC from source.


Role Variables
--------------

`ossec_dir: "/var/ossec"` is the directory where you want to install OSSEC

`ossec_version: "2.8.2"` is the version of OSSEC

`ossec_url: "https://github.com/ossec/ossec-hids/archive/{{ ossec_version }}.tar.gz"` is the url where to get OSSEC archive

`ossec_dl_dest: "/root"` is the directory where you want to copy, extract and compile OSSEC

`ossec_preloaded_vars`: is a list of variables for preloaded-vars.conf


Dependencies
------------

None

Example Playbook
----------------

```
---
- hosts: Ossec_Nodes
  sudo: yes
  roles:
   - role: valentinogagliardi.ossec-role
     ossec_version: "2.8.2"
     ossec_preloaded_vars: |
       USER_LANGUAGE="en"
       USER_NO_STOP="y"
       USER_INSTALL_TYPE="local"
       USER_ENABLE_EMAIL="n"
       USER_DIR="{{ ossec_dir }}"
       USER_UPDATE="n"
       USER_DELETE_DIR="y"
       USER_ENABLE_ACTIVE_RESPONSE="n"
       USER_ENABLE_SYSCHECK="y"
       USER_ENABLE_ROOTCHECK="y"
       USER_ENABLE_FIREWALL_RESPONSE="n"
       #### exit ? ###
     tags: ossec-role
```

License
-------

GNU General Public License Version 2

Author Information
------------------

Valentino Gagliardi - valentino.g@servermanaged.it
