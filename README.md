ssh-otp
=======

Installation
------------

Copy `ssh-otp` to `/usr/local/bin`:

    sudo mkdir -p /usr/local/bin
    sudo cp ssh-otp

Generate one-time password secret for current user:

    ssh-otp setup

Test your authenticator:

    ssh-otp test

If everything works, add the following line in your `/etc/ssh/sshd_config`:

    ForceCommand /usr/local/bin/ssh-otp login

And restart sshd:

    restart ssh

To disable otp for the current user:

    ssh-otp reset

