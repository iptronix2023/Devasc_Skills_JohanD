Task name: Task 2_Ansible
Task preparation:
	=>Lab 7.4.7: Use ansible
	=>Devasc VM
	=>CSR1000v VM
	=> VS Code
	=> configure ansible
Task implementation
	=> edit inventory hosts file
		# Enter the hosts or devices for Ansible playbooks
		CSR1kv ansible_user=cisco ansible_password=cisco123! ansible_host=192.168.56.101
	=> edit ansible.cfg file
		# config file for ansible-csr
		[defaults]
		#Use local hosts file in this folder
		inventory =./hosts
		host_key_checking = False # Don't worry about RSA Fingerprints
		retry_files_enabled = False # Do not create them
		depreciation_warnings = False # Do not show warnings

Task troubleshooting
	=> CSR1000v VM crashes during boot
	=> laptop lacks resources to run 2 VM's at the same time
	=> snapshot en cloon gemaakt van de VM's
	=> playbook errors because of tabs in the script

Task verification

ultimate playbook script: ios_facts

---
- name: ios_facts
  hosts: CSR1kv
  gather_facts: false
  connection: local
  
  tasks:
  - name: Run show version on remote devices
    ios_command:
      commands: 
        - show version
  - name: Gather L3 interfaces resource and minimal legacy facts
    ios_facts:
      gather_subset: 
        - min
      gather_network_resources: 
        - l3_interfaces
  - name: Configure buffer size
    ios_logging:
      aggregate:
        - { dest: console, level: notifications } 
        - { dest: buffered, size: 5000 } 
		
ansible output:

devasc@labvm:~/labs/devnet-src/ansible/ansible-csr1000v$ ansible-playbook ios_facts.yml -i hosts

PLAY [ios_facts] ******************************************************************************

TASK [Run show version on remote devices] *****************************************************
ok: [CSR1kv]

TASK [Gather L3 interfaces resource and minimal legacy facts] *********************************
[WARNING]: default value for `gather_subset` will be changed to `min` from `!config` v2.11
onwards
ok: [CSR1kv]

TASK [Configure buffer size] ******************************************************************
changed: [CSR1kv]

PLAY RECAP ************************************************************************************
CSR1kv                     : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  


