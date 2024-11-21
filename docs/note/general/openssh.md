# OpenSSH Server

Install OpenSSH Server

```bash
sudo apt install openssh-server
```

Configure the SSH server

```bash
sudo nano /etc/ssh/sshd_config
```

Check for and adjust existing occurrences of these configuration directives, or add new ones, as required:

```bash
PermitRootLogin no
PasswordAuthentication no
```

check the configuration after changing it and before restarting the server:

```bash
sudo sshd -t -f /etc/ssh/sshd_config
```

Restart the ssh service to pick up configuration changes:

```bash
sudo systemctl try-reload-or-restart ssh
```

import ssh key from github

```bash
ssh-import-id-gh <github-username>
```

In your host pc generate ssh key pair

```bash
ssh-keygen -t ed25519
```

can also add comment to the key

```bash
ssh-keygen -t ed25519 -C "renesas-ssh-key"
```

Connect to the server using ssh

```bash
ssh <username>@<server-ip>
```

Note: Check the server ip address using `ip a`

```bash
ip a
```
