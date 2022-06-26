First requirement vlan package
- `````sudo apt install vlan -y`````

Add requirement vlan kernel module
- `````sudo modprobe 8021q`````

In case we have ens160 and ens192. ens192 as trunk interface and we will add new vlan tag 101 with ip address 10.101.1.10/24

Edit file /etc/netplan/00-installer-config.yaml
- Adjust as below
  - `````network:`````
  - &ensp;`````ethernets:`````
  - &ensp;&ensp;`````ens160: {}`````
  - &ensp;&ensp;`````vlans:`````
  - &ensp;&ensp;&ensp;`````ens192.101:`````
  - &ensp;&ensp;&ensp;&ensp;`````id: 101`````
  - &ensp;&ensp;&ensp;&ensp;`````link: ens192`````
  - &ensp;&ensp;&ensp;&ensp;`````addresses: [10.101.1.10/24]`````

NOTES: YAML file is sensitive to space. Each block in YAML is separated by 2 spaces, so make sure you write it as above

Restart netplan
- `````sudo netplan apply`````
