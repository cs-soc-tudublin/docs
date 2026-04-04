---
title: Zabbix
created: 2026-02-26T11:42:47
modified: 2026-04-04T17:41:09
tags:
  - three
  - monitoring
---

# **Zabbix**

[Zabbix](https://www.zabbix.com/) is how we monitor and alert for our Cluster and VMs. We self host a Zabbix server on a dedicated container 

We have active Zabbix agents on our VMs

Hosted on [zabbix-ct](../two/containers/zabbix-ct)

## How to Install Zabbix

Make a Zabbix Directory ``/src/zabbix``

Then download the repository to it

[https://www.zabbix.com/download?zabbix=7.4&os_distribution=debian&os_version=12&components=agent_2&db=&ws=](https://www.zabbix.com/download?zabbix=7.4&os_distribution=debian&os_version=12&components=agent_2&db=&ws=)

## How to Setup Zabbix on VM

Open the .conf file

``sudo nano /etc/zabbix/zabbix_agent2.conf``

Change the Hostname:

``Hostname``=*vm_name*.vm.cspp.ie

Restart the service and check its running

``sudo systemctl restart zabbix-agent2``

``sudo systemctl status zabbix-agent2``

## How to Connect Zabbix to Web Server

[http://10.0.0.104/zabbix](http://10.0.0.104/zabbix) (Password in the password manager)

Monitoring -> Hosts

Find Template host (It should be disabled)

Click <u>Template</u> -> Host -> Clone (Bottom Right)

Change:

``Host name``=*vm_name*.vm.cspp.ie

``Visible name``=*Vm_name*

| ``Interfaces`` |          |                |                      |                   |          |
| -------------- | -------- | -------------- | -------------------- | ----------------- | -------- |
|                | **Type** | **IP address** | **DNS name**         | **Connect to**    | **Port** |
|                | Agent    | *vm_ip*        | *vm_name*.vm.cspp.ie | IP  \|  ***DNS*** | 10050    |

Scroll down

Tick **\[ \] Enabled**

Then Add.

Hover over "ZBX"

It should be green and say (Might take a minute):

Active checks Available

*vm_name*.vm.cspp.ie:10050 Available

## Full Install and Setup of Zabbix (Clean VM)

### Install

Make a Zabbix Directory ``/src/zabbix``

Then download the repository to it

[https://www.zabbix.com/download?zabbix=7.4&os_distribution=debian&os_version=12&components=agent_2&db=&ws=](https://www.zabbix.com/download?zabbix=7.4&os_distribution=debian&os_version=12&components=agent_2&db=&ws=)

### Configuration

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

`Host name`=*vm_name*.vm.cspp.ie

``Visible name``=*Vm_name*

``Templates``:

*Linux by Zabbix agent active*

*Docker by Zabbix agent 2*

*Systemd by Zabbix agent 2*

Other templates should be added depending on what is running on the VM

``Host groups``=Virtual machines

``Interfaces``

| Type  | IP address | DNS name             | Connect to        | Port  |
| ----- | ---------- | -------------------- | ----------------- | ----- |
| Agent | *vm_ip*    | *vm_name*.vm.cspp.ie | IP  \|  ***DNS*** | 10050 |

If the Zabbix agent is getting ``Docker: Service is down``, Zabbix needs to be given permissions to view the Docker Socket

``sudo usermod -aG docker zabbix``

``sudo systemctl restart zabbix-agent2``
