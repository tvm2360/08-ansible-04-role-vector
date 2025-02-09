# 📃 Role overview

## 08-ansible-04-role-vector

Description: Role install vector

| Field                | Value           |
|--------------------- |-----------------|
| Readme update        | 09/02/2025 |

### Defaults

**These are static variables with lower priority**

#### File: defaults/main.yml

| Var          | Type         | Value       |Required    | Title       |
|--------------|--------------|-------------|-------------|-------------|
| [vector_version](defaults/main.yml#L2)   | str   | `0.44.0` |    n/a  |  n/a |
| [vector_clickhouse_ip](defaults/main.yml#L3)   | str   | `172.17.0.2` |    n/a  |  n/a |


### Vars

**These are variables with higher priority**
#### File: vars/main.yml

| Var          | Type         | Value       |Required    | Title       |
|--------------|--------------|-------------|-------------|-------------|
| [vector_platform](vars/main.yml#L2)   | str   | `x86_64` |    n/a  |  n/a |
| [vector_directory](vars/main.yml#L3)   | str   | `/opt` |    n/a  |  n/a |


### Tasks


#### File: tasks/main.yml

| Name | Module | Has Conditions |
| ---- | ------ | --------- |
| Get and Unarchive vector distrib | ansible.builtin.unarchive | False |
| Move vector directory | command | False |
| Create systemd service Vector | copy | False |
| Enable and start Vector service | systemd | False |
| Get vector config | template | False |
| Flush handlers |  | False |


## Playbook

```yml
---
- hosts: localhost
  remote_user: root
  roles:
    - vector-role

```

## Author Information
tvm2360

#### License

MIT

#### Minimum Ansible Version

2.1

#### Platforms

- **Ubuntu**: [20.04]
