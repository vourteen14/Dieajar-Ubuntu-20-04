First requirement vlan package
- `````sudo apt install vlan -y`````

Add requirement vlan kernel module
- `````sudo modprobe 8021q`````

In case we have ens160 and ens192. ens192 as trunk interface and we will add new vlan tag 101 with ip address 10.101.1.10/24
Edit file /etc/netplan/00-installer-config.yaml
- Adjust as below
  - `````network:
  - `````  ethernets:
  - `````    ens160: {}`````
  - `````    vlans:`````
  - `````      ens192.101:`````
  - `````        id: 101`````
  - `````        link: ens192`````
  - `````        addresses: [10.101.1.10/24]`````

# NOTES: YAML file is sensitive to space

Restart netplan
- `````sudo netplan apply`````
