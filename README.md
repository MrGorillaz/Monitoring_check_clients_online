# check_clients_online
Nagios/Icinga Plugin to get Current Online Clients

DATE: 30.05.2016

Author: Alexander Orlowski

Description:

This plugin will output all clients of a subnet which are currently online

It will also display all clients which wore online in a specific time period

PerformanceData will be stored for Graphite/Grafana use.

"check_client_watch usage:"

./check_client_watch -sn IP-SUBNET -n SUBNETNAME -s NIGHTSTART -e NIGHTEND -c VALUE -w VALUE -x

"DESCRIPTION"

-sn or --subnet		: range of subnet to ping in CIDR-Format e.g. 192.168.1.0/24 *REQUIRED*

-n or --name		: name of subnet e.g. CLIENTS or WLAN *REQUIRED*

-s or --start		: time when nightwatch will start DEFAULT=0000 (00:00 AM) *OPTIONAL*

-e or --end		: time when nightwatch will end DEFAULT=0300 (03:00 AM) *OPTIONAL*

-w or --warning		: warning value for clients online at night DEFAULT=50

-c or --critical	: critical value for clients online at night DEFAULT=100

-x or --exclude		: hostnames or IPs which will be excluded from nightwatch by excludefile /tmp/exclude_hosts_$SUBNETNAME 

-h or --help      	: will print this Help

"EXAMPLE:"

./check_client_watch -sn 192.168.1.0/24 -n Clients -s 0000 -e 0300 -w 20 -c 50 -x

./check_client_watch --subnet 192.168.1.0/24 --name Clients --start 0000 --end 0300 --warning 20 --critical 50 --exclude

#!!! fping is required !!!

testet on Icinga2 @ Ubuntu 14.04
