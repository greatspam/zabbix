ZBX-ASTERISK-PJSIP
==================

A simple Asterisk template to monitor Asterisk servers using PJSIP.
Based on the original work of [Hieronymousch](https://github.com/hieronymousch/zabbix-asterisk-pjsip).

Requirements
------------

This template was tested for Zabbix 4.4 and higher.

on FreePBX server: 
- copy to /etc/zabbix/ZBX-ASTERISK-PJSIP/

- yum install zabbix40-agent.x86_64  jq.x86_64

- /etc/zabbix_agentd.conf : edit 
  - Server=<ip of zabbix server>
  - ServerActive=<ip of zabbix server>
  - Hostname=<hostname of asterisk>
  - AllowRoot=1
  - Include=/etc/zabbix/ZBX-ASTERISK-PJSIP/userparameters/asterisk_pjsip.userparameter.conf

- cat /etc/sudoers.d/zabbix
Defaults:zabbix !requiretty

zabbix ALL=(ALL:ALL)  NOPASSWD: /usr/sbin/asterisk, /usr/sbin/iptables, /usr/bin/ps, /usr/bin/sudo, /usr/bin/bash

- visudo -sc

- systemctl restart zabbix-agent

on Zabbix server:
- import template template-zbx-asterisk-pjsip.xml
- assign to host
- watch for errors:  sudo tail -f /var/log/zabbix/zabbix_server.log

License
-------

This template is distributed under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.

### Copyright

  Copyright (c) Sébastien Bourgeois

### Authors

  Sébastien Bourgeois
  (sb |at| altho |dot| st)
