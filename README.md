# Ansible Role: Gitea

**This role is based on [ansible-role-gogs] by [Jeff Geerling], author of [Ansible for DevOps].**

[![Build Status](https://travis-ci.org/ArgonQQ/ansible-role-gitea.svg?branch=master)](https://travis-ci.org/ArgonQQ/ansible-role-gitea)

Installs [Gitea], a Go-based front-end to Git, on RedHat or Debian-based linux systems.

After the playbook is finished, visit the Gitea server (on port 3000 by default), and you will be redirected to the /install page, where you can configure an administrator account and other default options.

## Requirements

Requires git (via `geerlingguy.git`), and at least the Gitea HTTP port (3000 by default) open on your system's firewall. Install MySQL (e.g. via `geerlingguy.mysql`) prior to installing Gitea if you would like to use MySQL instead of built-in SQLite support.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    gitea_user: git
    gitea_user_home: /home/git

The user and home under which Gitea will run and be installed.

    gitea_version: 1.4.2

Gitea version for install and for easy upgrade (`1.4.2`)

    gitea_binary_url: https://github.com/go-gitea/gitea/releases/download/v1.1.4/gitea-1.1.4-linux-amd64

Download URL for the Gitea binary. (`https://github.com/go-gitea/gitea/releases/download/v{{ gitea_version }}/gitea-{{ gitea_version }}-linux-amd64`)

    gitea_binary_sig_url: https://github.com/go-gitea/gitea/releases/download/v1.1.4/gitea-1.1.4-linux-amd64.sha256

Download URL for the SHA256 checksum to verify binary. (`"{{ gitea_binary_url }}.sha256"`)

    gitea_http_port: "3000"

HTTP port over which Gitea will be accessed.

    gitea_use_mysql: false
    gitea_db_name: gitea
    gitea_db_username: gitea
    gitea_db_password: root

MySQL database support. Set `gitea_use_mysql` to `true` to configure MySQL for Gitea, using the database name, username, and password defined by the respective variables.

## Dependencies

  - geerlingguy.git

## Example Playbook

    - hosts: servers
      vars_files:
        - vars/main.yml
      roles:
        - noplanman.gitea

*Inside `vars/main.yml`*:

    gitea_http_port: "8080"

## License

MIT / BSD

[Gitea]: https://github.com/go-gitea/gitea/
[ansible-role-gogs]: https://github.com/geerlingguy/ansible-role-gogs
[Jeff Geerling]: https://www.jeffgeerling.com/
[Ansible for DevOps]: https://www.ansiblefordevops.com/
