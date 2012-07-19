mohu_locallinux
===============

The purpose of this repository is to collaborate on a readme which provides staff with instructions on how to set up their local boxes.

Firstly, download [http://www.ubuntu.com/download/server](ubuntu server) and install it on VMWare (we are curently using version 4).

Once you have this you see that you have a command line inside a window. What you really want is to connect with SSH.

For the sake of simplicity, everyone should have a user called mohu as their primary user.

### Update apt-get package manager

```bash
sudo apt-get update
```

### Install SSH server

```bash
sudo apt-get install openssh-server
```

### Create the mohu user and grant sudo

When prompted for a password use fj, for full name use Mohu. Ignore the rest.
```bash
sudo adduser mohu
sudo usermod -G sudo mohu
```


### Connect from your mac terminal

In your ubuntu window find out your ip address

```bash
ifconfig | grep 'inet '
```

This should return two lines, the local 127.0.0.1 IP and the one you actually want.

Now, from your mac terminal, try to SSH in.

```bash
ssh mohu@192.168.0.2
```

### Install build tools, version control, screen and mysql

```bash
sudo apt-get install linux-kernel-headers build-essential git-core mysql-server libmysqlclient15-dev libmysql++-dev wget curl libpcre3-dev libssl-dev lsof python-setuptools python-dev screen
```
When prompted to create passwords for mysql just hit enter as it is a local machine.



