mohu_locallinux
===============

The purpose of this repository is to collaborate on a readme which provides staff with instructions on how to set up their local boxes.

Firstly, download [http://www.ubuntu.com/download/server](ubuntu server, 12.04 LTS) and install it on VMWare (we are curently using version 4).

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

### Install build tools, version control, screen, vim, mysql and nginx

```bash
sudo apt-get install linux-kernel-headers build-essential git-core mysql-server libmysqlclient15-dev libmysql++-dev wget curl libpcre3-dev libssl-dev lsof python-setuptools python-dev screen vim nginx
```
When prompted to create passwords for mysql just hit enter as it is a local machine.

You'll need to give screen the correct permissions too.

```bash
sudo chmod a+rxw /dev/pts/0
```

### Set defaults for mysql

Stop the MySQL Server:

```bash
sudo service mysql stop
```

The edit it's configuration file:

```bash
sudo vim /etc/mysql/my.cnf
```

Ensure the following is in the configuration file:

```
character-set-server=utf8
default-storage-engine=innodb
```
Start MySQL:

```bash
sudo service mysql start
```

### Install the Python Virtual Environment

```bash
sudo easy_install setuptools
sudo apt-get install python-pip
sudo pip install --upgrade pip
sudo pip install --upgrade virtualenv
sudo pip install --upgrade virtualenvwrapper
```

Make a folder for the virtual environments:

```bash
mkdir ~/.virtualenvs
```

The make sure the following is in your `~/.bashrc`:

```bash
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python
export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
export PIP_VIRTUALENV_BASE=$WORKON_HOME
export PIP_RESPECT_VIRTUALENV=true
```

When it is, reload your `~/.bashrc` file:

```bash
source ~/.bashrc
```

### Install fabric

```bash
sudo apt-get install fabric
```

### Install node, npm, stylus and coffeescript

For development it is most convenient to install to the user's home folder to avoid having to sudo.
We will use the most recent stable version, so please update as needed.

```bash
cd ~
mkdir src
cd src
export NODE_VERSION='0.6.18'
wget http://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION.tar.gz
tar xvfz node-v$NODE_VERSION.tar.gz
cd node-v$NODE_VERSION
./configure --prefix=~/local
make install
cd ~/src
```

Now for npm, coffeescript and stylus, if you need them

```bash
curl http://npmjs.org/install.sh | sudo sh
sudo npm install -g coffee-script
sudo npm install -g stylus
```

Now for express and socket.io, if you need them

```bash
sudo npm install -g express
sudo npm install -g socket.io
```


