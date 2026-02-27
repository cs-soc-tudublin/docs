---
title: Zabbix
created: 2026-02-26T11:42:47
modified: 2026-02-26T11:49:21
tags:
   - Monitoring
---

**TODO**

Install Zabbix
[https://www.zabbix.com/download?zabbix=7.4&os_distribution=debian&os_version=12&components=agent_2&db=&ws=](https://www.zabbix.com/download?zabbix=7.4&os_distribution=debian&os_version=12&components=agent_2&db=&ws=)

Connect to Web Interface (Active Monitoring)
[https://www.zabbix.com/documentation/7.4/en/manual/guides/monitor_linux](https://www.zabbix.com/documentation/7.4/en/manual/guides/monitor_linux)

You need to open the ports on UFW for the Zabbix Server to be able to listen
``sudo ufw allow from 10.0.0.104 to any port 10050 proto tcp``
(IP of the Zabbix Server and the port Zabbix uses)

``sudo nano /etc/zabbix/zabbix_agent2.conf``

Change the conf to
``Server``=10.0.0.104
``ServerActive``=10.0.0.104
``Hostname``=*vm_name*

```systemctl restart zabbix-agent2```

When creating the host on the web interface, use the templates:
*Linux by Zabbix agent active*
*Docker by Zabbix agent 2*
*Systemd by Zabbix agent 2*

Others should be added depending on what is running on the VM

Interfaces

| Type  | IP address | DNS name           | Connect to      | Port  |
| ----- | ---------- | ------------------ | --------------- | ----- |
| Agent | *vm_ip*    | *vm_ip*.vm.cspp.ie | **IP**  \|  DNS | 10050 |
