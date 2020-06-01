## Timx workspace setup
![CI](https://github.com/sweetim/workspace-setup/workflows/CI/badge.svg)
![Ansible-galaxy](https://img.shields.io/ansible/quality/48993)

This will automatically setup to timx-style workspace

### Installation

- autojump
- history using directional key
- bash_it (modern theme)
- VIM
- nvm
- rust
- python

### Usage

```
ansible-galaxy install sweetim.workspace_setup
ansible localhost -m include_role -a name=sweetim.workspace_setup --diff --ask-become
```

or using ansible-playbook

```
---
- name: sample
  hosts: 127.0.0.1
  roles:
  - role: sweetim.workspace_setup
    bash_it_theme: "modern"

```
