---
title: Zabbix
created: 2026-02-26T11:42:47
modified: 2026-02-26T11:49:21
tags:
  - three
  - monitoring
---
# **Zabbix**

[Zabbix](https://www.zabbix.com/) is how we monitor and alert for our Cluster and VMs. We self host a Zabbix server on a dedicated container 

We have active Zabbix agents on our VMs

Hosted on [zabbit-ct](../two/containers/zabbix-ct)

## How to Install and Setup Zabbix
[https://www.zabbix.com/download?zabbix=7.4&os_distribution=debian&os_version=12&components=agent_2&db=&ws=](https://www.zabbix.com/download?zabbix=7.4&os_distribution=debian&os_version=12&components=agent_2&db=&ws=)

Connect to Web Interface (Active Monitoring)
[https://www.zabbix.com/documentation/7.4/en/manual/guides/monitor_linux](https://www.zabbix.com/documentation/7.4/en/manual/guides/monitor_linux)

You need to open a port on UFW for the Zabbix CT to send passive requests
``sudo ufw allow from 10.0.0.104 to any port 10050 proto tcp``
(IP of the Zabbix Server and the port passive Zabbix uses)

``sudo nano /etc/zabbix/zabbix_agent2.conf``

Change the config to
``Server``=10.0.0.104
``ServerActive``=10.0.0.104
``Hostname``=*vm_name*.vm.cspp.ie

``sudo systemctl restart zabbix-agent2``

When creating the host on the web interface, 
``Host name``=*vm_name*.vm.cspp.ie
``Visible name``=Vm_name

``Templates``:
*Linux by Zabbix agent active*
*Docker by Zabbix agent 2*
*Systemd by Zabbix agent 2*
Other templates should be added depending on what is running on the VM

``Host groups``=Virtual machines

``Interfaces``

| Type  | IP address | DNS name           | Connect to        | Port  |
| ----- | ---------- | ------------------ | ----------------- | ----- |
| Agent | *vm_ip*    | *vm_ip*.vm.cspp.ie | IP  \|  ***DNS*** | 10050 |
