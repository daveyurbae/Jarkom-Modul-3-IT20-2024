# Jarkom-Modul-3-IT20-2024
Write-up pengerjaan soal shift modul 3 praktikum Jaringan Komputer kelompok IT20

## Anggota Kelompok
1. George David Nebore (5027221043)
2. solo mode :)

## Topologi Kelompok IT20 Praktikum Modul 3

![Topologi](https://github.com/user-attachments/assets/d6198d69-cd57-4520-a2ba-f6382ee0bb5e)

## Konfigurasi

### Paradis (DHCP Relay)

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.243.1.0
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.243.2.0
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.243.3.0
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 192.243.4.0
	netmask 255.255.255.0

```

### Tybur (DHCP Server)

```
auto eth0
iface  eth0 inet static
  address 192.243.4.1
  netmask 255.255.255.0
  gateway 192.243.4.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Fritz (DNS Server)

```
aauto eth0
iface  eth0 inet static
  address 192.243.4.2
  netmask 255.255.255.0
  gateway 192.243.4.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Warhammer (Database)

```
auto eth0
iface  eth0 inet static
  Address 192.243.3.3
  netmask 255.255.255.0
  gateway 192.243.3.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Beast ( LoadBalancer Laravel)

```
auto eth0
iface  eth0 inet static
  address 192.243.3.1
  netmask 255.255.255.0
  gateway 192.243.3.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Colossal (LoadBalancer PHP)

```
auto eth0
iface  eth0 inet static
  address 192.243.3.2
  netmask 255.255.255.0
  gateway 192.243.3.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Annie (Laravel Worker)

```
auto eth0
iface  eth0 inet static
  address 192.243.1.1
  netmask 255.255.255.0
  gateway 192.243.1.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Bertholdt (Laravel Worker)

```
auto eth0
iface  eth0 inet static
  address 192.243.1.2
  netmask 255.255.255.0
  gateway 192.243.1.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Reiner (Laravel Worker)

```
auto eth0
iface  eth0 inet static
  address 192.243.1.3
  netmask 255.255.255.0
  gateway 192.243.1.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Armin (PHP Worker)

```
auto eth0
iface  eth0 inet static
  address 192.243.2.1
  netmask 255.255.255.0
  gateway 192.243.2.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Eren (PHP Worker)

```
auto eth0
iface  eth0 inet static
  address 192.243.2.2
  netmask 255.255.255.0
  gateway 192.243.2.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Mikasa (PHP Worker)

```
auto eth0
iface  eth0 inet static
  address 192.243.2.3
  netmask 255.255.255.0
  gateway 192.243.2.0

up echo nameserver 192.168.254.128 > /etc/resolv.conf
```

### Zeke (Client)

```
auto eth0
iface  eth0 inet dhcp

up echo nameserver 192.168.254.128 > /etc/resolv.conf
up echo nameserver 192.168.254.128 >> /etc/resolv.conf

```

### Erwin (Client Tetap)

```
auto eth0
iface  eth0 inet dhcp
hwaddress ether 5a:e2:87:8f:a3:40

up echo nameserver 192.243.4.1 > /etc/resolv.conf
up echo nameserver 192.168.254.128 >> /etc/resolv.conf

```

## Bash Install

- Paradis (DHCP Relay)

```sh
apt-get update
apt-get install isc-dhcp-relay -y
```

- Tybur (DHCP Server)

```sh
echo nameserver 192.168.254.128 > /etc/resolv.conf
apt-get update
apt-get install isc-dhcp-server -y
dhcpd --version

echo INTERFACES="eth0" > /etc/default/isc-dhcp-serverm
```

- Fritz (DNS Server)

```sh
echo nameserver 192.168.254.128 > /etc/resolv.conf
apt-get update
apt-get install bind9 -y
```

- Warhammer (Database)

```sh
echo nameserver 192.168.254.128 > /etc/resolv.conf

apt-get update
apt-get install mariadb-server -y
service mysql start
```

- Beast (LoadBalancer Laravel)

  **No script soal tidak ada soal**

- Colossal (LoadBalancer PHP)

```sh
echo nameserver 192.168.254.128 > /etc/resolv.conf

apt-get update
apt-get install apache2-utils php7.3 php-fpm -y
apt-get install nginx -y
apt-get install lynx -y
```

- Annie , Bertholdt, Reiner (Laravel Worker)

  **No script soal tidak ada soal**

- Armin, Eren, Mikasa (PHP Worker)

```sh
echo nameserver 192.243.2.1 >> /etc/resolv.conf

apt-get update
apt-get install nginx -y
apt-get install lynx -y
apt-get install php php-fpm -y
apt-get install wget -y
apt-get install unzip -y
service nginx start
service php7.3-fpm start

```