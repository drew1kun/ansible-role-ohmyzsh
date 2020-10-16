Ansible role: ohmyzsh
=========

[![MIT licensed][mit-badge]][mit-link]
[![Galaxy Role][role-badge]][galaxy-link]

Cross-platform ansible role for installing and configuring zsh with [oh-my-zsh][ohmyzsh]

There is a choice between [powerlevel10k][powerlevel10k] and [powerlevel9k][powerlevel9k]
Default oh-my-zsh theme is powerlevel10k

If only `p10k` is set to `yes`, then `p9k` will not be installed and configured.
It is not recommended to set `p9k` only to `yes`, because it's slow).
If both `p9k` and `p10k` are set to `yes`, then `p10k` will be used but the `p9k` style will be sourced.
If installed both, but want to turn `p9k` off, then comment the following line in ~/.zshrc:

	source ${HOME}/.zsh/omz_powerlevel9k.cfg

In combination with [ansible-macos_terminal role](https://github.com/drew-kun/ansible-macos_terminal) getting the following results(assuming you are using p9k or p10k+p9k combo):

![alt text](https://github.com/drew-kun/ansible-ohmyzsh/blob/master/imgs/iterm2_ohmzsh.png "iTerm2")


Requirements
------------

NOTE: Role requires Fact Gathering by ansible!

One of the following OS (or deriviatives):
 - Debian | Ubuntu
 - MacOS (with [Homebrew][homebrew])

For MacOS:
if Homebrew is not installed on the managed host, install the following role via galaxy:

    ansible-galaxy install geerlingguy.homebrew

 And include it in the playbook:

```yaml
roles:
- geerlingguy.homebrew
```

Role Variables
--------------
OS-Agnostic:

| Variable | Description | Default |
|----------|-------------|---------|
| **ohmyzsh_install_dir** | Directory oh-my-zsh to be installed in | `/usr/local/share/ohmyzsh` |
| **ohmyzsh_custom_aliases** | File containing custom shell config | `$HOME/.zsh/aliases.local` |
| **ohmyzsh_powerlevel10k** | Whether to install powerlevel10k theme or not | `yes` |
| **ohmyzsh_powerlevel9k** | Whether to install powerlevel9k theme or not | `yes` |
| **ohmyzsh_powerlevel9k_cfg** | Path to powerlevel9k config file | `${HOME}/.zsh/omz_powerlevel9k.cfg` |
| **ohmyzsh_users[]** | List of users to install zsh/oh-my-zsh for | see [`defaults/main.yml`](defaults/main.yml) |
| **ohmyzsh_default_theme** | Default theme to be configured for users which do not have theme specified | `robbyrussell` |
| **ohmyzsh_default_plugins[]** | The list of plugins for oh-my-zhs to be installed | see [`defaults/main.yml`](defaults/main.yml) |
| **ohmyzsh_custom_plugins[]** | The list of custom plugins for oh-my-zhs to be installed | see [`defaults/main.yml`](defaults/main.yml) |

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

```yaml
- hosts: dev_clients_macos
  gather_facts: yes
  roles:
  - geerlingguy.homebrew
  - drew-kun.ohmyzsh
```

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
[powerlevel10k]: https://github.com/romkatv/powerlevel10k
