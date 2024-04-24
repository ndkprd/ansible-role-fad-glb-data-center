# ansible-role-fortiadc-glb-data-center

## Description

Ansible role to create/update Fortinet's FortiADC GLB Data Center entries using REST API.

## Usage

### Install Role

```
ansible-galaxy install ndkprd.fad_glb_data_center
```

### Hosts Example

```
[fortiadc]
fad-01 ansible_host=fad-01.infra.ndkprd.com ansible_connection=local fad_apitoken=mysupersecrettoken fad_vdom=root
```

### Playbook Example

```
---

- name: Update/create FortiADC resources.
  hosts: all
  become: false
  gather_facts: false
  connection: local
  vars:
    # global-load-balance data-center entries
    fad_glb_data_centers:
      - name: dc0.ndkprd.com
        location: ID
      - name: dc1.ndkprd.com
        location: ID
      - name: dc2.ndkprd.com
        location: ID

  roles:
    - ndkprd.fad_glb_data_center

```

### About Tags

Each task is tagged with their task file name, `fad_glb_data_center`.

There's also a some kind of pre-task and post-task that run before and after create/update tasks to compare the value of before and after create/update tasks, tagged with the above tag and an additional `debug` tag.

## Limitation

Only developed and tested against FortiADC 7.0.

## License

MIT, use at your own risk.
