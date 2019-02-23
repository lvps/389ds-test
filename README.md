# 389DS test

Vagrant config and Ansible playbook to install 389 Directory Service and configure it automatically.

## Enabling the admin server

Uncomment the extra role and tasks in `playbook.yml` and provision the VM.

Then `vagrant ssh` and run `setup-ds-admin.pl`, which will create a new instance. I still haven't figured out how to automate that part.

Then open a browser, head to localhost:9830 and try to log in to the admin console: you may find that "the server is down" and an helpful
button to bring it up. Press it.

If you want to connect from the remote admin console tool thing (`389-console` on Arch Linux, it's in the AUR) run this on the *host*:

`iptables -t nat -A OUTPUT -o lo -p tcp --dport 389 -j REDIRECT --to-port 1389`

And connect to `localhost:9830` in the admin console on the host machine. This is needed because there's a web server at port 9830 that
tells the admin console to connect to port 389. However, Vagrant forwards port 389 from the VM to port 1389 on the host since it cannot
bind ports < 1024.
