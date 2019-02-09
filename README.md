# OpenDJ test

Vagrant config and Ansible playbook to install 389 Directory Service and configure it automatically.

The Ansible playbook creates an inf file (with plaintext admin password, so maybe add a task to remove it) which is fed to the setup script.

The setup script returns successfully and starts 389DS, but the ServerRoot setting is completely ignored, nothing is ever created in that directory.

On the plus side: a `/etc/dirsrv/slapd-whetever` is created.
