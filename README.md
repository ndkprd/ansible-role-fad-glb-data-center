# ansible-role-fortiadc-glb-data-center

## Description

Ansible role to create/update Fortinet's FortiADC GLB Data Center entries using REST API.

## Usage

### Install Role

```
ansible-galaxy install ndkprd.fortiadc-glb-data-centers
```

### Variables

#### Host Vars

| Variable | Data Type | Default Value | Explanation |
|----------|-----------|---------------|-------------|
| fad_vdom | str | root | Target FAD's VDOM. |
| fad_apitoken | str | - | Target FAD's API Key. |

#### Group Vars

| Variable | Data Type | Default Value | Explanation |
|----------|-----------|---------------|-------------|
| fad_glb_data_centers | array | [] | List of Data Centers. |
| fad_glb_data_centers[x].name | str | - | Data Center name, used as `mkey` in request body. |
| fad_glb_data_centers[x].location | str | ZZ | 2-letter country ID. |

### Hosts Example

```
[fortiadc]
fad-01 ansible_host=fad-01.infra.ndkprd.com ansible_connection=local fad_apitoken=mysupersecrettoken fad_vdom=root
```

> **ℹ Note:** almost all tasks are in the form of API Request from localhost, so the `ansible_connection=local` is a must. But for better abstractions, you can remove that and put the `connection: local` in Playbook instead.

### Playbook Example

```
---

- name: Update/create FortiADC GLB Data Centers resources.
  hosts: all
  become: false
  gather_facts: no
  # connection: local
  vars:
    fad_glb_data_centers:
      - name: dc1.ndkprd.com
        location: ID
      - name: dc2.ndkprd.com
        location: ID
      - name: dc3.ndkprd.com
        location: ID

  roles:
    - ndkprd.fortiadc-glb-data-centers

```

### About Tags

Every task in this role is tagged with `fad_glb_data_centers`, with 2 task (one before, one after) is also tagged with `debug` to check initial and post-task value. You can skip out the debug with `--skip-tags debug`

For example, if you're using CLI, you can just go `ansible-playbook -i hosts playbook.yaml --skip-tags debug`.

## Limitation

Only developed and tested against FortiADC 7.0.

## License

MIT, use at your own risk.
