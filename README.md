## timx workspace setup

![CI](https://github.com/sweetim/workspace-setup/workflows/CI/badge.svg)
![ansible-downloads](https://img.shields.io/ansible/role/d/sweetim/workspace_setup?style=flat-square&label=download&logo=ansible&logoColor=%23F00&color=brightgreen)

This will automatically setup to timx-style workspace

### Components

- dependencies
- autojump
- history using directional key
- starship
- vim
- mise
- nodejs
- bun
- rust
- python
- uv
- docker

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

### Configuration

The components installed are controlled by `workspace_setup_components`
(defaults to all of them). Pass a subset to install only what you need:

```bash
ansible localhost -m include_role -a name=sweetim.workspace_setup --diff -K \
  -e workspace_setup_components='["vim","starship"]'
```

#### Available selections for `workspace_setup_components`

The following values are valid entries for the `workspace_setup_components`
list:

| Component      | Description                                        |
| -------------- | -------------------------------------------------- |
| `dependencies` | APT packages required by the other components      |
| `autojump`     | `autojump` directory jumper                        |
| `history`      | Shell history navigation with the directional keys |
| `starship`     | Starship cross-shell prompt                        |
| `vim`          | VIM plus the plugin set listed below               |
| `mise`         | mise version manager (runs before rust/nodejs/bun) |
| `python`       | Python 3 toolchain                                 |
| `uv`           | uv Python package/project manager                  |
| `rust`         | Rust toolchain (via mise)                          |
| `nodejs`       | Node.js toolchain (via mise)                       |
| `bun`          | Bun runtime (via mise)                             |
| `docker`       | Docker engine and compose plugin                   |

#### Examples

Install everything except Docker:

```bash
ansible localhost -m include_role -a name=sweetim.workspace_setup --diff -K \
  -e workspace_setup_components='["dependencies","autojump","history","starship","vim","mise","python","uv","rust","nodejs","bun"]'
```

Install only the editor and prompt:

```bash
ansible localhost -m include_role -a name=sweetim.workspace_setup --diff -K \
  -e workspace_setup_components='["vim","starship"]'
```

> **Note:** Order matters. `mise` must come before `rust`, `nodejs` and `bun`,
> which install their toolchains through it. The default order already handles
> this, so only reorder if you know what you are doing.

### Dependencies

```bash
apt install ansible
```

### Installation

```bash
ansible-galaxy install sweetim.workspace_setup
ansible localhost -m include_role -a name=sweetim.workspace_setup --diff -K
```

**Note (Ubuntu 26.04+):** Ubuntu 26.04 ships `sudo-rs` as the default `sudo`,
whose become prompt Ansible cannot recognize (it times out). This role's
`ansible.cfg` points Ansible at the classic C sudo (`/usr/bin/sudo.ws`). If you
run outside this repo, pass it explicitly:

```bash
ansible localhost -m include_role -a name=sweetim.workspace_setup --diff -K -e ansible_sudo_exe=/usr/bin/sudo.ws
```

or using ansible-playbook

```yaml
---
- name: sample
  hosts: 127.0.0.1
  roles:
      - role: sweetim.workspace_setup
```
