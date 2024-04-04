# ansible-role-fortiadc-glb-data-center

## Description

Ansible role to create/update Fortinet's FortiADC GLB Data Center entries using REST API.

## Usage

### Install Role

```
ansible-galaxy install ndkprd.fortiadc-glb-data-center
```

### Hosts Example

```
fad1.ndkprd.com fad_apitoken=my-supersecret-token
fad2.ndkprd.com fad_apitoken=my-supersecret-token
```

### Vars Example

```
---
fad_vdom: root

fad_glb_data_centers:
  - name: dc1.ndkprd.com # Data Center name
    location: ID # 2 letters country ID
  - name: dc2.ndkprd.com
    location: ID
```

### Playbook Example

```
---
# ./playbook.yaml

- name: Setup GLB Data Center entry in FortiADC.
  hosts: fortiadc
  become: false
  gather_facts: no
  vars_files:
    - ./fad-glb-dc-vars.yaml

  roles:
    - ndkprd.fortiadc-glb-data-center

```

## Limitation

Developed and tested against FortiADC 7.0.

## License

MIT, use at your own risk.