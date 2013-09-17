ssh-otp
=======

Installation
------------

Copy `ssh-otp` to `/usr/local/bin`:

    sudo mkdir -p /usr/local/bin
    sudo cp ssh-otp

Add the following line in your `/etc/ssh/sshd_config`:

    ForceCommand /usr/local/bin/ssh-otp login

And restart sshd:

    restart ssh


Enable
------

Generate one-time password secret for current user:

    ssh-otp setup

Test your authenticator:

    ssh-otp test


Disable
-------

To disable otp for the current user:

    ssh-otp reset


Non-interactive commands
------------------------

To use commands like `scp`, you need to pass in the one-time password
through a `OTP` environment variable.

In `/etc/ssh/sshd_config`, add `OTP` to the list of `AcceptEnv`:

    AcceptEnv OTP

On the client machine, instruct ssh to send the `OTP` environment by adding
the following in your `~/.ssh/config`:

    Host *
    SendEnv OTP

Now set the `OTP` environment before sending the command over ssh:

    OTP="123456" scp server:~/.ssh/authorized_key .

