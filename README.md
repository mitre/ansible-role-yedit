# Ansible Module: Yedit

This repository contains an Ansible module for modifying YAML files.

Forked to preserve file mode when using yedit.

## Install

You can install the `mitre.yedit` role via Ansible Galaxy:

```
ansible-galaxy install mitre.yedit
```

If you do this, you should also add a `requirements.yml` so other users of your playbook know what dependencies to install:

```yaml
# requirements.yml
roles:
  - src: mitre.yedit
```

## Examples

Managing `.yml` files might be necessary for configuration management. Here's how you can use the Yedit module in an Ansible playbook:

```yaml
# playbook.yml
- hosts: localhost
  roles:
    - role: mitre.yedit
  tasks:
    - name: manage yaml files
      yedit:
        src: /tmp/test.yaml
        key: a.b.c
        value: { d: { e: { f: "this is a test" } } }

    - name: get a specific value
      yedit:
        src: /tmp/test.yaml
        state: list
        key: a.b.c.d.e.f
      register: yeditout

    - debug: var=yeditout
```

## Development

To incorporate this role into your Ansible setup, simply place it into any directory that Ansible recognizes as a role directory. For further details on embedding modules and plugins within roles and using module utilities, refer to the Ansible documentation links provided:

- [Embedding Modules and Plugins In Roles](http://docs.ansible.com/ansible/devel/playbooks_reuse_roles.html#embedding-modules-and-plugins-in-roles)
- [module_utils](http://docs.ansible.com/ansible/latest/intro_configuration.html#module-utils)

## Documentation

Comprehensive documentation is directly available in the role's library file on GitHub. You can access it [here](https://github.com/mitre/ansible-role-yedit/blob/main/library/yedit.py#L15).
