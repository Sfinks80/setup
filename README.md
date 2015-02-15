# Setup
Setup new VPS step-by-step

#### Resolving "perl: warning: Setting locale failed."
```shell
locale-gen ru_RU ru_RU.UTF-8
dpkg-reconfigure locales
```

#### Create new user with groups sudo & www-data
```shell
adduser --home /home/sfinks username
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