Role Name
=========

Ansible role to partition an disk, LV or not, in Linux systems.

Requirements
------------

Ansible>=2.1

Role Variables
--------------

  disk_devices:
    - disk: /dev/nvme0n1
      device: /dev/nvme0n1
      lv: yes
      fs_type: ext4
      mount_opts: defaults,nobootwait
      mount_state: mounted
      mount: /opt/

    disk_lvol:
    - vg_name: vg_opt
      vg_pv: /dev/nvme0n1
      lv_dev:
        - device: /dev/vg_opt/opt
          name: data
          size: '100%VG'
          force: yes
          fs_type: ext4
          mount_opts: defaults,nobootwait
          mount_state: mounted
        mount: /data/

Dependencies
------------

None

Example Playbook
----------------

    - name: Playbook sample to disk partition
      hosts: host-test
      become: yes
      gather_facts: yes

      roles:
        - disk-part

License
-------

[Apache-2.0](https://github.com/chaordic/ansible-role-disk-part/blob/master/LICENSE)

Author Information
------------------

Chaordic Systems, Cloud Team.
