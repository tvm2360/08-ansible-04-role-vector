# Роль Vector (08-ansible-04-role-vector)

Описание: Роль устанавливает Vector

| Field                | Value           |
|--------------------- |-----------------|
| Readme update        | 09/02/2025 |

### Defaults: Статические переменные с низким приоритетом

#### Файл: defaults/main.yml

| Var          | Type         | Value       |Required    | Title       |
|--------------|--------------|-------------|-------------|-------------|
| [vector_version](defaults/main.yml#L2)   | str   | `0.44.0` |    n/a  |  n/a |
| [vector_clickhouse_ip](defaults/main.yml#L3)   | str   | `172.17.0.2` |    n/a  |  n/a |

### Vars: Статические переменные с высоким приоритетом

#### Файл: vars/main.yml

| Var          | Type         | Value       |Required    | Title       |
|--------------|--------------|-------------|-------------|-------------|
| [vector_platform](vars/main.yml#L2)   | str   | `x86_64` |    n/a  |  n/a |
| [vector_directory](vars/main.yml#L3)   | str   | `/opt` |    n/a  |  n/a |

### Tasks: Задания

#### File: tasks/main.yml

| Name | Module | Has Conditions |
| ---- | ------ | --------- |
| Get and Unarchive vector distrib | ansible.builtin.unarchive | False |
| Move vector directory | command | False |
| Create systemd service Vector | copy | False |
| Enable and start Vector service | systemd | False |
| Get vector config | template | False |
| Flush handlers |  | False |

```mermaid
flowchart TD
Start
classDef block stroke:#3498db,stroke-width:2px;
classDef task stroke:#4b76bb,stroke-width:2px;
classDef includeTasks stroke:#16a085,stroke-width:2px;
classDef importTasks stroke:#34495e,stroke-width:2px;
classDef includeRole stroke:#2980b9,stroke-width:2px;
classDef importRole stroke:#699ba7,stroke-width:2px;
classDef includeVars stroke:#8e44ad,stroke-width:2px;
classDef rescue stroke:#665352,stroke-width:2px;

  Start-->|Task| Get_and_Unarchive_vector_distrib0[get and unarchive vector distrib]:::task
  Get_and_Unarchive_vector_distrib0-->|Task| Move_vector_directory1[move vector directory]:::task
  Move_vector_directory1-->|Task| Create_systemd_service_Vector2[create systemd service vector]:::task
  Create_systemd_service_Vector2-->|Task| Enable_and_start_Vector_service3[enable and start vector service]:::task
  Enable_and_start_Vector_service3-->|Task| Get_vector_config4[get vector config]:::task
  Get_vector_config4-->|Task| Flush_handlers5[flush handlers]:::task
  Flush_handlers5-->End
```

## Сценарий

```yml
---
- hosts: localhost
  remote_user: root
  roles:
    - vector-role

```

## Автор

tvm2360

#### Лицензия

MIT

#### Минимальная верия ansible

2.10

#### Платформы

- **Ubuntu**: [20.04]


