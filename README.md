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

When prompted for a password use fj
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