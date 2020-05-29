# Zabbix Bind9 Statistics Collection

This method utilises Bind 9s built in statistics export via HTTP/XML.

Most statistics available are collected, several aggregate graphs are defined.

[Forked from https://github.com/Pesticles/Zabbix-Bind9-Statistics-Collection](https://github.com/Pesticles/Zabbix-Bind9-Statistics-Collection)

## Requirements
* Zabbix 4.X / Zabbix 5.X
* Python 3

## To install:
* Configure Bind to export statistics via HTTP by adding the following to your named.conf and restarting bind:
```
statistics-channels {
 	inet 127.0.0.1 port 58053 allow { 127.0.0.1; };
};
```
* Copy the userparameter_rr_bind.conf into your zabbix agents include directory (/etc/zabbix/zabbix_agentd.d/ on
Debian 10)
* Copy the script bind-stats-rr.py to /etc/zabbix/script/
userparameter_bind.conf)
* Import the xml template into Zabbix
```
mkdir /etc/zabbix/script
mv /***/bind-stats-rr.py /etc/zabbix/script
chown zabbix. /etc/zabbix/script
```
## Note:

You can enable per-zone statistics (which will be automatically discovered) by adding the following clause to each zone definition in your named.conf.local:
`zone-statistics yes;`
