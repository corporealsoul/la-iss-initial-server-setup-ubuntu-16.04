### Platform,

`anup@ubuntu-16047:~$ cat /etc/os-release`

`anup@ubuntu-16047:~$ hostnamectl`

`anup@ubuntu-16047:~$ lsb_release -a`

<br>

### Change hostname,

`anup@ubuntu-16047:~$ sudo nano /etc/hostname`

    ubuntu-16047

`anup@ubuntu-16047:~$ sudo nano /etc/hosts`

    127.0.0.1 localhost
    127.0.1.1 ubuntu-16047
    
    # The following lines are desirable for IPv6 capable hosts
    ::1     ip6-localhost ip6-loopback
    fe00::0 ip6-localnet
    ff00::0 ip6-mcastprefix
    ff02::1 ip6-allnodes
    ff02::2 ip6-allrouters

`anup@ubuntu-16047:~$ hostnamectl`

`anup@ubuntu-16047:~$ getent hosts`

<br>

### Configure static IP,

`anup@ubuntu-16047:~$ sudo nano /etc/cloud/cloud.cfg.d/subiquity-disable-cloudinit-networking.cfg`

    network: {config: disabled}


`anup@ubuntu-16047:~$ sudo cp /etc/netplan/00-installer-config.yaml /etc/netplan/00-installer-config.yaml.backup`

`anup@ubuntu-16047:~$ sudo nano /etc/netplan/00-installer-config.yaml`

    # This is the network config written by 'subiquity'
    network:
      version: 2
      renderer: networkd
      ethernets:
        enp0s3:
          dhcp4: yes
        enp0s8:
          addresses: [192.168.56.10/24]
          dhcp4: false

`anup@ubuntu-16047:~$ sudo netplan try`

`anup@ubuntu-16047:~$ sudo netplan apply`

<br>

### Update,

`anup@ubuntu-16047:~$ sudo apt-get update`

`anup@ubuntu-16047:~$ sudo apt-get upgrade`

<br>

### System Information,

`anup@ubuntu-16047:~$ uname -a`

<br>

### Users information,

`anup@ubuntu-16047:~$ less /etc/passwd`

<br>

### Creating a New User,

`anup@ubuntu-16047:~$ adduser ubuntu-user`

`anup@ubuntu-16047:~$ usermod -aG sudo ubuntu-user`

`anup@ubuntu-16047:~$ finger ubuntu-user`

<br>

### Groups information,

`anup@ubuntu-16047:~$ less /etc/group`

<br>

### Resources,

**RAM,** `anup@ubuntu-16047:~$ free -h`

**CPU,** `anup@ubuntu-16047:~$ lscpu`

**Load,** `anup@ubuntu-16047:~$ htop`

**Drive,** `anup@ubuntu-16047:~$ df -h`

<br>

### Processes,

`anup@ubuntu-16047:~$ ps -aux`

`anup@ubuntu-16047:~$ htop`

<br>

### Services / Daemons (d),

`anup@ubuntu-16047:~$ systemctl list-unit-files`

`anup@ubuntu-16047:~$ systemd-cgtop`

`anup@ubuntu-16047:~$ ps -eo 'tty,pid,comm' | grep ^?` , Processes per Services / Daemons

<br>

### Ports,

**Note :** Port, (2^16)-1, or 1-65535 are available, and ports in range 1-1023 are the privileged ones.

`anup@ubuntu-16047:~$ sudo lsof -i -P -n | grep LISTEN`

`anup@ubuntu-16047:~$ sudo netstat -tulpn | grep LISTEN`

<br>

### Firewall,

`anup@ubuntu-16047:~$ sudo ufw status`

`anup@ubuntu-16047:~$ sudo ufw enable`

`anup@ubuntu-16047:~$ sudo ufw allow OpenSSH`

`anup@ubuntu-16047:~$ sudo ufw allow 22`

`anup@ubuntu-16047:~$ sudo ufw app list`

`anup@ubuntu-16047:~$ sudo ufw status`

<br>

### Install basic system utilities,

`anup@ubuntu-16047:~$ sudo apt-get install software-properties-common`

`anup@ubuntu-16047:~$ sudo apt-get install htop`

`anup@ubuntu-16047:~$ sudo apt-get install multitail`

<br>

### Logs,

`anup@ubuntu-16047:~$ ls -ltr /var/log`

<br>

### List of repos,

`anup@ubuntu-16047:~$ cat /etc/apt/sources.list`

<br>
