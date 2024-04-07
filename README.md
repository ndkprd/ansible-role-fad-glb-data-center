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
[fortiadc]
fad1.ndkprd.com fad_apitoken=my-super-secrettoken
fad2.ndkprd.com fad_apitoken=my-super-secrettoken
```

### Playbook Example

```
---
# ./playbook.yaml

- name: Setup GLB Data Center entry in FortiADC.
  hosts: fortiadc
  become: false
  gather_facts: no
  vars:
    fad_vdom: root
    fad_glb_data_centers:
      - name: dc1.ndkprd.com # Data Center name
        location: ID # 2 letters country ID
      - name: dc2.ndkprd.com
        location: ID

  roles:
    - ndkprd.fortiadc-glb-data-center

```

### About Tags

I added quiet lots of debug task, mainly to check if the variable I set is correct. These tags basically just print out the var that the previous task set/register. You can skip them altogether by skipping tasks with `debug` tags.

For example, if you're using CLI, you can just go `ansible-playbook playbook.yaml --skip-tags debug`.

## Limitation

Only developed and tested against FortiADC 7.0.

## License

MIT, use at your own risk.
