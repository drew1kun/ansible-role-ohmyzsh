ohmyzsh
=========

Cross-platform ansible role for installing and configuring zsh with ![oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

Default oh-my-zsh theme: ![powerlevel9k](https://github.com/bhilburn/powerlevel9k)

Requirements
------------

One of the following OS (or deriviatives):
 - Debian | Ubuntu
 - MacOS

The role installs parted and raspi-config packages as dependencies

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

When used against MacOS hosts, then depends on:
 - homebrew

Example Playbook
----------------

    - hosts: macos
      roles:
         - ohmyzsh

License
-------

MIT

Author Information
------------------

Andrew Shagayev
