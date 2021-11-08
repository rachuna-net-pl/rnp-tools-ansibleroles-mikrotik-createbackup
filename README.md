rnp-tools-ansibleroles-mikrotik-createbackup
=========

Ansible Role - Mikrotik - Create backup

![Overwiew](https://gitlab.com/rachuna-net.pl/tools/ansibleroles/mikrotik/rnp-tools-ansibleroles-mikrotik-createbackup/-/raw/develop/docs/createBackup.png)

Requirements
------------

```
apt-get install sshpass
```

```
apt-get install python3-pip
pip install paramiko
```

Vagrant create test
```
vagrant plugin uninstall vagrant-routeros
vagrant ssh -- /ip address add address=192.168.33.100/24 interface=ether2 network=192.168.33.100
vagrant ssh -- /user set admin password=admin
```


Role Variables
--------------

Defaults role values:

```yaml
input_role_localhost_os_distribution: "ubuntu"
input_role_ansible_host:             "{{ ansible_host }}"
input_role_destination_path:          "/tmp/test"
input_role_ansible_user:              "{{ ansible_user }}"
input_role_ansible_password:          "{{ ansible_ssh_pass }}"
```

Role vars:
```yaml
var_role_backup_filename:      "{{ input_role_ansible_host }}.{{ lookup('pipe','date +%Y%m%d') }}.backup"
var_role_backup_filename_rsc:  "{{ input_role_ansible_host }}.{{ lookup('pipe','date +%Y%m%d') }}.rsc"
```



Example Playbook
----------------

```yaml
- hosts: all
  gather_facts: yes
  tasks:

  - include_role:
      name: ../../
    vars:
      input_role_localhost_os_distribution: "{{ ansible_distribution }}"
      input_role_ansible_host:              "{{ ansible_host }}"
      input_role_destination_path:          "/tmp/test"
      input_role_ansible_user:              "{{ ansible_user }}"
      input_role_ansible_password:          "{{ ansible_ssh_pass }}"
```

License
-------

BSD 3-Clause

Author Information
------------------

### Maciej Rachuna
SysOps/DevOps
