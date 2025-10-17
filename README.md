## timx workspace setup
![CI](https://github.com/sweetim/workspace-setup/workflows/CI/badge.svg)
![ansible-downloads](https://img.shields.io/ansible/role/d/sweetim/workspace_setup?style=flat-square&label=download&logo=ansible&logoColor=%23F00&color=brightgreen)

This will automatically setup to timx-style workspace

### Components

- autojump
- history using directional key
- starship
- vim
- mise
- nodejs
- rust
- python3
- pip3
- uv

### VIM plugins

- VIM Vundle
- nerdtree
- nerdtree-git-plugin
- vim-gitgutter
- vim-rainbow
- airline/vim-airline
- vim-fugitive
- indentLine
- vim-one

### Dependencies

```bash
apt install ansible
```

### Installation

```bash
ansible-galaxy install sweetim.workspace_setup
ansible localhost -m include_role -a name=sweetim.workspace_setup --diff --ask-become
```

or using ansible-playbook

```yaml
---
- name: sample
  hosts: 127.0.0.1
  roles:
  - role: sweetim.workspace_setup
```
