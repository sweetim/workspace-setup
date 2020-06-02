## Timx workspace setup
![CI](https://github.com/sweetim/workspace-setup/workflows/CI/badge.svg)
![Ansible-galaxy](https://img.shields.io/ansible/quality/48993)
![ansible-downloads](https://img.shields.io/ansible/role/d/48993?color=brightgreen&label=downloads)

This will automatically setup to timx-style workspace

### Installation

- autojump
- history using directional key
- bash_it (modern theme)
- vim
- nvm
- rust
- python3
- pip3

### VIM plugins

- VIM Vundle
- nerdtree
- nerdtree-gitplugin
- vim-rainbow
- airline/vim-airline
- vim-fugitive
- indentLine
- vim-one

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
