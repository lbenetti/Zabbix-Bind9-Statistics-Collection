# Zabbix Bind9 Statistics Collection

This method utilises Bind 9s built in statistics export via HTTP/XML.

Most statistics available are collected, several aggregate graphs are defined.

[Forked from https://github.com/Pesticles/Zabbix-Bind9-Statistics-Collection](https://github.com/Pesticles/Zabbix-Bind9-Statistics-Collection)

## Requirements
* Zabbix 4.X / Zabbix 5.X
* Python 3

## To install:
* Configure Bind to export statistics via HTTP by adding the following to your <b>named.conf</b> and restarting bind:
```
statistics-channels {
 	inet 127.0.0.1 port 58053 allow { 127.0.0.1; };
};
```
* Copy the <b>userparameter_rr_bind.conf</b> into your zabbix agents include directory (<b>/etc/zabbix/zabbix_agentd.d/</b> on Debian 10)
* Copy the script <b>bind-stats-rr.py</b> to <b>/etc/zabbix/script/</b>
userparameter_bind.conf)
* Import the xml template into Zabbix
```
mkdir /etc/zabbix/script
mv /***/bind-stats-rr.py /etc/zabbix/script
chown zabbix. /etc/zabbix/script
```
## Note:

You can enable per-zone statistics (which will be automatically discovered) by adding the following clause to each zone definition in your <b>named.conf.local</b>:
`zone-statistics yes;`
