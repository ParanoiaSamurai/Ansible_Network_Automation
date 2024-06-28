# Network Automation with Ansible

This repository contains Ansible playbooks for automating network tasks on Cisco IOS devices. The playbooks perform various tasks such as configuring interfaces, managing VLANs, saving and backing up configurations, and gathering device facts.

## Prerequisites

1. Ansible installed on your control machine.
2. `ansible` and `netmiko` Python libraries installed.
3. SSH access to the Cisco devices.
4. An inventory file with device details.

## Setting Up the Inventory File

Create an inventory file (`hosts`) with details of the devices you want to manage.

``` bash
[routers]                                              
                                                        
host name                         
                                                        
[routers:vars]                                         
                                                        
ansible_user = "username"
ansible_password = "password"                          
ansible_connection = network_cli #type of interface that you want to use                       
ansible_network_os = ios # type of OS the device is using
ansible_port = 22
```

## Creating playbooks to play along. 
You can find the playbooks that I have used in playbook directory. Here is an example of playbook:

```bash
$ ansible-playbook -i hosts ~/Desktop/ansible_playbooks/interface_information.yml 

PLAY [Gather Interface Information from Cisco IOS device] **********************************************************

TASK [Gather interface facts] **************************************************************************************
ok: [devnetsandboxiosxe.cisco.com]

TASK [Display interface facts] *************************************************************************************
ok: [devnetsandboxiosxe.cisco.com] => {
    "interfaces.ansible_facts.ansible_net_interfaces": {
        "GigabitEthernet1": {
            "bandwidth": 1000000,
            "description": "Configured by Ansible",
            "duplex": "Full",
            "ipv4": [
                {
                    "address": "10.10.20.48",
                    "subnet": "24"
                }
            ],
            "lineprotocol": "up",
            "macaddress": "0050.56bf.bfe7",
            "mediatype": "Virtual",
            "mtu": 1500,
            "operstatus": "up",
            "type": "vNIC"
        },
        "GigabitEthernet2": {
            "bandwidth": 1000000,
            "description": "NETCONF-CONFIGURED PORT",
            "duplex": "Full",
            "ipv4": [
                {
                    "address": "12.12.12.2",
                    "subnet": "24"
                }
            ],
            "lineprotocol": "up",
            "macaddress": "0050.56bf.82f3",
            "mediatype": "Virtual",
            "mtu": 1500,
            "operstatus": "up",
            "type": "vNIC"
        },
        "GigabitEthernet3": {
            "bandwidth": 1000000,
            "description": "Son Konfig Netconf",
            "duplex": "Full",
            "ipv4": [
                {
                    "address": "13.13.13.13",
                    "subnet": "24"
                }
            ],
            "lineprotocol": "up",
            "macaddress": "0050.56bf.32cf",
            "mediatype": "Virtual",
            "mtu": 1500,
            "operstatus": "up",
            "type": "vNIC"
        },
        "Loopback0": {
            "bandwidth": 8000000,
            "description": null,
            "duplex": null,
            "ipv4": [
                {
                    "address": "10.0.0.1",
                    "subnet": "24"
                }
            ],
            "lineprotocol": "up",
            "macaddress": null,
            "mediatype": null,
            "mtu": 1514,
            "operstatus": "up",
            "type": null
        },
        "Loopback1": {
            "bandwidth": 8000000,
            "description": "Network to 101",
            "duplex": null,
            "ipv4": [
                {
                    "address": "1.1.1.1",
                    "subnet": "32"
                }
            ],
            "lineprotocol": "up",
            "macaddress": null,
            "mediatype": null,
            "mtu": 1514,
            "operstatus": "up",
            "type": null
        },
        "Loopback10": {
            "bandwidth": 8000000,
            "description": null,
            "duplex": null,
            "ipv4": [],
            "lineprotocol": "up",
            "macaddress": null,
            "mediatype": null,
            "mtu": 1514,
            "operstatus": "up",
            "type": null
        },
        "Loopback123": {
            "bandwidth": 8000000,
            "description": "configured by JM",
            "duplex": null,
            "ipv4": [
                {
                    "address": "192.168.100.100",
                    "subnet": "24"
                }
            ],
            "lineprotocol": "up",
            "macaddress": null,
            "mediatype": null,
            "mtu": 1514,
            "operstatus": "up",
            "type": null
        },
        "Loopback2662": {
            "bandwidth": 8000000,
            "description": "Added by DaddyZ",
            "duplex": null,
            "ipv4": [
                {
                    "address": "10.2.3.26",
                    "subnet": "24"
                }
            ],
            "lineprotocol": "up",
            "macaddress": null,
            "mediatype": null,
            "mtu": 1514,
            "operstatus": "up",
            "type": null
        },
        "Loopback66": {
            "bandwidth": 8000000,
            "description": null,
            "duplex": null,
            "ipv4": [
                {
                    "address": "7.10.7.10",
                    "subnet": "24"
                }
            ],
            "lineprotocol": "up",
            "macaddress": null,
            "mediatype": null,
            "mtu": 1514,
            "operstatus": "up",
            "type": null
        },
        "VirtualPortGroup0": {
            "bandwidth": 333000,
            "description": null,
            "duplex": null,
            "ipv4": [
                {
                    "address": "192.168.1.1",
                    "subnet": "24"
                }
            ],
            "lineprotocol": "up",
            "macaddress": "001e.7a85.31bd",
            "mediatype": null,
            "mtu": 1500,
            "operstatus": "up",
            "type": "Virtual Port Group"
        }
    }
}

PLAY RECAP *********************************************************************************************************
devnetsandboxiosxe.cisco.com : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   ```
