# pcw-ansible
PCW Ansible playbooks and collections 

| Collection  | Description |
| ----------- | ----------- |
| edgeos      | Playbooks for managing ERX/edgeos router configuration       |
| monitor   | prom, grafana playbooks |

# How to use 
* Install python deps
```shell
    uv sync
```

* Install ansible collections:
```shell
    ansible-galaxy collection install -r requirements.yml
```

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