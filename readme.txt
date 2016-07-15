# Debian Web Server Construction Guide on HP ProLiant DL 360
2014 or more older information

## Prepare

* Download iso image "debian-x.x.x.-amd64-DVD-1.iso"
* Burn to USB memory using USBWriter.exe

## Turn power on

### Config ROM-base utility

* Adjust time to UTC
* Config as you like

### Config integrated Lights-Out (iLO)

* Network

### Config HP Smart Array Controller

* RAID

## Install Debian

* Choose "Graphical Expert Install" mode
* Select "Additional Locale" en_US.UTF-8
* Select "System Locale" en_US.UTF-8
* Select "Keymapping" same as your keyboard type
* Ignore "Installer Components to load"
* Insert USB memory including network adapter driver file has name like bnx2/bnx2-mips-00-0.0.0a.fw. If prompt doesn't continue, make sure usb memory format is FAT32, and created bnx2/ directry at usb memory root.
* Select "Primary Network Interface" eth0
* Select "Auto configurate network settings?" no
* Input "eth0 IP"
* Input "Hostname"
* Ignore "Domain Name"
* Select "Shadow Password" yes
* Select "Permit Root Login" no
* Input "Username" proper
* Input "Passwprd" proper
* Select "Use NTP" yes
* Select "NTP server" default, and reconfigure after install
* Select "Timezone" UTC
* Select "Partitioning" Guide mode, use whole disk LVM, no Encrypt, All file in one partition
* Input "VolumeGroup Name" vg1
* Select "Kernel" linux-image-amd64
* Select "initrd drivers" General Purpose
* Select "Use Network Mirror" no
* Select "PackageManager" security updates, release updates
* Select "Program Select" Utilities
* Select "Force Install GRUB to EFI Removable device" no
* Select "Is set SystemTime to UTC" yes

## Config Debian after install done

* Close unsecure ports `purge exim4, exim4-base, rpcbind`
* Stop unnecessary services
* Stop beep sound (modprobe.d)
* Check locale
* Setup /etc/apt
* Setup motd
* Setup sysctl, `sysctl -p`
* Setup sysv-rc-conf
* Setup /etc/hosts
* Setup /etc/resolve.conf
* Setup /etc/dhcp/dhclient.conf
* Setup iptables
* Setup tc
* Setup PPPoE
* Run `apt-get update`
* Run `apt-get upgrade`
* Run `apt-get dist-upgrade`
* Setup automation of APT Upgrade security repositry
* Setup chkrootkit
* Setup nologin
* Setup openssh-server
* Setup git
* Create git repositry on /etc/
* Setup zsh
* Setup vim
* Setup sudo
* Setup dotfiles
* Setup gdebi
* Setup curl
* Setup ntpd
* Setup nginx
* Setup mysql
* Setup php5-common php5-fpm php5-apcu php5-cli php5-curl php5-imagick php5-mysqlnd php5-json php5-dev
* Setup composer
* Setup igbinary
* Setup nodejs
* Setup rsyslog
* Setup logwatch
* Setup /etc/fstab
* Setup cifs-utils
* Setup backup script
