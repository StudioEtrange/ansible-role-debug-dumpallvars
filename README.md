Debug Dump All Vars
===================


Dump all variables to a file on the remote host and/or on the guest host.

This may be useful when debugging Ansible roles. Most Ansible variables will be written to a file on the remote host.


This role is a mix between https://github.com/ome/ansible-role-debug-dumpallvars and https://github.com/mrjk/ansible-role-dumpall

Role Variables
--------------

	dumpall_keep_on_guest: no
	dumpall_keep_on_host: yes
	
    debug_dumpallvars_file_guest_destination: "/tmp/ansible-debug-dumpallvars-guest-{{ inventory_hostname }}.txt"
    debug_dumpallvars_file_host_destination: "/tmp/ansible-debug-dumpallvars-host-{{ inventory_hostname }}.txt"

The `dumpall_keep_on_guest` and `dumpall_keep_on_host` variables let you choose where you want to keep the dump file. The default setting is to keep files only on Ansible host.

The `debug_dumpallvars_file_guest_destination` variable is where the dump file is created on the target. The `debug_dumpallvars_file_host_destination` is where all dumps are retrieved from target.

All variables are mandatory ( except for `debug_dumpallvars_file_host_destination` ), and they are documented in default/main.yml.


Example Playbook
----------------

Example with a host_destination will result in a dumpfile /examine/ansible.all on the host machine:
(the dumpfile on the guest is removed)

    - hosts: localhost
      roles:
        - role: debug_dumpallvars
		  dumpall_keep_on_guest: yes
          debug_dumpallvars_file_host_destination: /tmp/my_prj



