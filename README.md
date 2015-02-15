# Setup
Setup new VPS step-by-step

#### Resolving "perl: warning: Setting locale failed."
```shell
locale-gen ru_RU ru_RU.UTF-8
dpkg-reconfigure locales
```

#### Create new user with groups sudo & www-data
```shell
adduser --home /home/username username
adduser username sudo
adduser username www-data
```

#### Disable ssh password login
```shell
vim /etc/ssh/sshd_config
```
```config
ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no
```
```shell
service ssh restart
```

#### Auth username by key
```shell
cd /home/username
mkdir ./.ssh
chown username:username ./.ssh
echo 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDLxni6D/FepIez+QP6zBfwRAmVRXxggbUBYeoSro0LczC5+GhUb1HIeoSXCOV6WojuuKjxftbi9AqFD5b22d0b13ndsgWJxyB81bK9Txh7rb8yKeZP69fPFmxLAYtu6cTxHUui7r3y4XXqOnmmXodt7wlCKkm6s8ITMGUWaDabBMt70h/2sW9uUyP3sBYDtziX4SB9DAMx1rclgqXgo7TbViplcisL5QSfKxnN+TYZDja5wgvJKxonHZg6oJpEF4MzonbfDeDi+SSc+Nvv0UPkBQX3ZzDKsOrYaPV8Nf7IzEIWUS9iB13jl3CiHkAV48pqRuRGZwSEdKa0A+RRQBpz username@ubuntu' >> authorized_keys
chown username:username ./authorized_keys
exit
```

