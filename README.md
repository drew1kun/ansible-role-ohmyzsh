Ansible role: ohmyzsh
=========

[![MIT licensed][mit-badge]][mit-link]
[![Galaxy Role][role-badge]][galaxy-link]

Cross-platform ansible role for installing and configuring zsh with [oh-my-zsh][ohmyzsh]

Default oh-my-zsh theme: [powerlevel9k][powerlevel9k]

Requirements
------------

NOTE: Role requires Fact Gathering by ansible!

One of the following OS (or deriviatives):
 - Debian | Ubuntu
 - MacOS (with [Homebrew][homebrew])

For MacOS:
if Homebrew is not installed on the managed host, install the following role via galaxy:

    ansible-galaxy install drew-kun.homebrew

 And include it in the playbook:

    roles:
        - drew-kun.homebrew

Role Variables
--------------
OS-Agnostic:

| Variable | Description | Default |
|----------|-------------|---------|
| **ohmyzsh_install_dir** | Directory oh-my-zsh to be installed in | `/usr/local/share/ohmyzsh` |
| **ohmyzsh_custom_aliases** | File containing custom shell config | `$HOME/.zsh/aliases.local` |
| **ohmyzsh_powerlevel9k** | Whether to install powerlevel9k theme or not | `yes` |
| **ohmyzsh_users[]** | List of users to install zsh/oh-my-zsh for | see [`defaults/main.yml`](defaults/main.yml) |
| **ohmyzsh_default_theme** | Default theme to be configured for users which do not have theme specified | `robbyrussell` |
| **ohmyzsh_default_plugins[]** | The list of plugins for oh-my-zhs to be installed | see [`defaults/main.yml`](defaults/main.yml) |

OS-Specific:

| Variable | Description | Default |
|----------|-------------|---------|
| **ohmyzsh_root_dir** | Root directory | <ul><li>Darwin: `/var/root`</li><li>Debian: `/root`</li></ul> |
| **ohmyzsh_home_dir** | User's home directory | <ul><li>Darwin: `/Users/`</li><li>Debian: `/home/`</li></ul> |
| **ohmyzsh_zprofile_dir** | Zsh profile directory | <ul><li>Darwin: `/etc/`</li><li>Debian: `/etc/zsh/`</li></ul> |

Dependencies
------------

None

Example Playbook
----------------

    - hosts: dev_clients_macos
      gather_facts: yes
      roles:
         - drew-kun.homebrew
         - drew-kun.ohmyzsh

License
-------

[MIT][mit-link]

Author Information
------------------

Andrew Shagayev | [e-mail](mailto:drewshg@gmail.com)

[role-badge]: https://img.shields.io/badge/role-drew--kun.ohmyzsh-green.svg
[galaxy-link]: https://galaxy.ansible.com/drew-kun/ohmyzsh/
[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[mit-link]: https://raw.githubusercontent.com/drew-kun/ansible-ohmyzsh/master/LICENSE
[homebrew]: http://brew.sh/
[ohmyzsh]: https://github.com/robbyrussell/oh-my-zsh
[powerlevel9k]: https://github.com/bhilburn/powerlevel9k
