# Ubuntu 20.04 - tinc

	sudo apt update
	sudo apt install tinc

## Configuration

tinc needs the following for it to work:

1. A network name. (In this sample, we'll call it NETNAME)
2. Configuration files. Namely: tinc.conf, tinc-up, tinc-down
3. Public/Private keys.
4. Host configuration files. These are distributed with the public key.
5. One to act as the main host everyone else will connect to.
	Main Host = HOST
	Other Hosts = CLIENTS##

## Main Host

	$ sudo mkdir -p /etc/tinc/NETNAME/hosts
	$ sudo vi /etc/tinc/NETNAME/tinc.conf

	Name = HOST
	AddressFamily = ipv4
	Interface = tun0

	$ sudo vi /etc/tinc/NETNAME/hosts/HOST

	Address = HOSTNAME_PUBLIC_IP
	Subnet = 10.0.0.1/32

Generate the public/private key pair for this host:

	sudo tincd -n NETNAME -K4096

	$ sudo vi /etc/tinc/NETNAME/tinc-up

	#!/bin/sh
	ifconfig $INTERFACE 10.0.0.1 netmask 255.255.255.0

	$ sudo vi /etc/tinc/NETNAME/tinc-down

	#!/bin/sh
	ifconfig $INTERFACE down

	$ sudo chmod 755 /etc/tinc/NETNAME/tinc-*

## Other Hosts

	$ sudo mkdir -p /etc/tinc/NETNAME/hosts
	$ sudo vi /etc/tinc/NETNAME/tinc.conf

	Name = CLIENTS##
	AddressFamily = ipv4
	Interface = tun0
	ConnectTo = HOST

	$ sudo vi /etc/tinc/NETNAME/hosts/CLIENTS##
*CHANGE THE IP ADDRESS FOR EACH HOST.*

	Subnet = 10.0.0.2/32

	$ sudo tincd -n NETNAME -K4096

	$ sudo vi /etc/tinc/NETNAME/tinc-up
*CHANGE THE IP ADDRESS FOR EACH HOST.*

	#!/bin/sh
	ifconfig $INTERFACE 10.0.0.2 netmask 255.255.255.0

	$ sudo vi /etc/tinc/NETNAME/tinc-down

	#!/bin/sh
	ifconfig $INTERFACE down

	$ sudo chmod 755 /etc/tinc/NETNAME/tinc-*

## Distribute the Keys

Easiest: just copy all the hosts files to every node.

## Enable the Network to Start on Boot

### If SystemV:

	$ sudo vi /etc/tinc/nets.boot

Add the NETNAME to this file.

### If SystemD:

	$ sudo systemctl enable tinc
	$ sudo systemctl start tinc
	$ sudo systemctl enable tinc@NETNAME
	$ sudo systemctl start tinc@NETNAME
