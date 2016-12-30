Ansible Attic Role
==================

An ansible role for installing and configuring Attic Backup.
The installation happens from source (picked up from git). So git needs to be present as a dependency role or ad it to the attic_dependency_pkgs variable.
You have 3 main sections in this role:

* installation of dependencies and Attic installation
* installation of the "server" part. This will create a dedicated user and set a public key on that user. This is the place where you can store your backups (remotely if you like)
* installation of the "client" part. This will set a private key on a dedicated backup user (for instance root), install the keychain manager so you can connect remotely and set a backup script for your backups + cronjob to execute the backup script

For more information on Attic, [visit the Attic website](https://attic-backup.org)

Role Variables
--------------

```yaml
attic_dependency_pkgs: list of dependency packages
attic_git_repo: git repo url of attic
attic_version: attic version number
attic_install_command: installation command
attic_server_install: boolean. If you want to run server.yml tasks
attic_client_install: boolean. If you want to run client.yml tasks
attic_user: details of the dedicated attic user ( used by your backup server )
attic_backup_user: details of the dedicated backup user ( used by your client server )
attic_ssh_config: ssh config details
attic_cron: cron to execute your backup script
```

View the default vars - defaults/main.yml - for a more detailed example.

Example Playbook
-------------------------

```yaml
- hosts: servers
  roles:
     - { role: MichaelRigart.attic, become: true }
```

License
-------

GPLv3

Author Information
------------------

Michaël Rigart <michael@netronix.be>
