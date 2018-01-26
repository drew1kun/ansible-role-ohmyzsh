Ansible role: ohmyzsh
=========

[![MIT licensed][mit-badge]][mit-link]
[![Galaxy Role][role-badge]][galaxy-link]

Cross-platform ansible role for installing and configuring zsh with [oh-my-zsh][ohmyzsh]

Default oh-my-zsh theme: [powerlevel9k][powerlevel9k]

Requirements
------------

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

    - ohmyzsh_install_dir               # directory oh-my-zsh to be installed in
    - ohmyzsh_custom_aliases            # file containing custom shell config
    - ohmyzsh_powerlevel9k: true|false  # whether to install powerlevel9k theme or not
    - ohmyzsh_users                     # list of users to install zsh/oh-my-zsh for
        - user:
          theme:                        # theme to be configured for user (if not specified the default theme will be configured)
          state: present|absent         # whether install or remove oh-my-zsh configuration for user

    - ohmyzsh_default_theme             # default theme to be configured for users which do not have theme specified
    - ohmyzsh_default_plugins           # the list of plugins for oh-my-zhs to be installed

OS-Specific:

    - ohmyzsh_root_dir                  # root directory
    - ohmyzsh_home_dir                  # user's home directory
    - ohmyzsh_zprofile_dir              # zsh profile directory

Dependencies
------------

None

Example Playbook
----------------

    - hosts: dev_clients_macos
      roles:
         - drew-kun.homebrew
         - drew-kun.ohmyzsh

License
-------

[MIT][mit-link]

Author Information
------------------

![Andrew Shagayev](drewshg@gmail.com)

[role-badge]: https://img.shields.io/badge/role-drew--kunohmyzsh-green.svg
[galaxy-link]: https://galaxy.ansible.com/drew-kun/ohmyzsh/
[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[mit-link]: https://raw.githubusercontent.com/drew-kun/ansible-ohmyzsh/master/LICENSE
[homebrew]: http://brew.sh/
[ohmyzsh]: https://github.com/robbyrussell/oh-my-zsh
[powerlevel9k]: https://github.com/bhilburn/powerlevel9k
