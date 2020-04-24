ansible-role-ceph-pools
=======================

![](https://github.com/kevincoakley/ansible-role-ceph-pools/workflows/Molecule%20Test/badge.svg)

Manage Ceph Erasure Coded and Replicated Pools - Tested on Ceph Nautilus 

Requirements
------------

Ceph cluster running the Nautilus release, preferably deployed using [ceph-ansible](https://github.com/ceph/ceph-ansible) 

Role Variables
--------------

See defaults/main.yml

Dependencies
------------

None

Example Playbook
----------------

    - name: Converge
      hosts: all
      become: true
    
      vars:
        cluster: ceph
        mon_group_name: mons
        erasure_code_profile:
          ec-profile:
            k: 2
            m: 1
            crush_failure_domain: host
        erasure_pool:
          erasure_pool:
            pg_num: 64
            erasure_code_profile: ec-profile
            application: rgw
        replicated_pool:
          replicated_pool:
            pg_num: 64
            application: rgw
    
      roles:
        - role: ansible-role-ceph-pools

License
-------

BSD

Author Information
------------------

Kevin Coakley (https://github.com/kevincoakley)