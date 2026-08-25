# edgeos-ansible 
Collection of Ansible roles for configuring a Ubiquiti Edgerouter X

# How to use 
* install ansible via pip/package manager
```shell
uv init /
uv add ansible  
```

* write inventory in `inventory.yaml` 

* Ping test your inventory 
```shell
uv run ansible-inventory --list -i inventory.yaml
```

* Run a given playbook with a given inventory 
```shell
uv run ansible-playbook -i inventory.yaml playbook.yaml
```

# Future improvements
* tags to only run certain tasks for each play 
* for greenfield erxes, sshd is not listening by default - is there a way to get around this? 
* the last step appears to hang since the ssh connection is dropped once the interface change is committed and saved ; maybe worth adding another task to reconnect with the new IP to ensure the changover went over ok?

----
# basic router config 
* open ssh 
* change lan subnet 

 - cannot run ansible from a world-writable dir 
 - create user "ansible" and chown 
- that didnt work 

- manually set location of ansible.cfg with 
EXPORT ANSIBLE_CFG = ... 

erxes dont have python on them anymore? 
they have python 2.7 
- https://forum.ansible.com/t/ansible-core-requires-a-minimum-of-python2-version-2-7-or-python3-version-3-5-current-version-2-6-6/3312/8 
downgrade to ansible-core 2.19 for python 2.7 support 
https://github.com/ansible-community/ansible-build-data/blob/main/9/CHANGELOG-v9.rst
https://docs.ansible.com/projects/ansible/latest/reference_appendices/release_and_maintenance.html 
https://pypi.org/project/ansible/#history

v3.0 edgeos also only has python 2.7 
user~$ show system image     
The system currently has the following image(s) installed:

v3.0.0.5842787.250718.1058     (running image) (default boot) 
v2.0.9-hotfix.7.5622731.230615.0857 

user:~$ which python 
/usr/bin/python
user@host:~$ python --version
Python 2.7.13

install paramiko
  329  uv add paramiko
https://github.com/paramiko/paramiko/issues/1936#issuecomment-981122850


# Helpful resources: 
builtins - https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/index.html 

run a script - https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/script_module.html#ansible-collections-ansible-builtin-script-module

pop a shell - https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/shell_module.html 

defining your inventory 
https://docs.ansible.com/projects/ansible/latest/inventory_guide/index.html 

https://github.com/metamesh/ansible-role-amazon-cloudwatch-agent

https://old.reddit.com/r/ansible/comments/1dqtjlu/edgeos_support/

https://community.ui.com/questions/Scripting-in-Edgeos/e8137e93-01f0-4985-8f36-418d5ce4818d

https://help.uisp.com/hc/en-us/articles/22591243128215-EdgeRouter-Run-Operational-Mode-Command-from-Scripts

https://github.com/nycmeshnet/vpn-infra 

https://github.com/nycmeshnet/nycmesh-ansible?tab=readme-ov-file

https://github.com/ppouliot/ansible-role-ubnt_platform_mgmt/blob/master/README.md

https://community.ui.com/questions/Auto-Provisioning/610c4afb-5228-4b27-9a0e-6cb23ebb0540

https://community.ui.com/questions/Best-practice-for-managing-thirty-EdgeRouters/20accc9e-0459-40e0-900e-cac163e68251?reply=3

https://hoop.dev/blog/the-simplest-way-to-make-ansible-ubiquiti-work-like-it-should/ 



