Subnet Range Calculator and Mikrotik VLAN Script Generator
You can view this WebApp by going to the following URL:

https://html-preview.github.io/?url=https://raw.githubusercontent.com/AshCooperUK/Subnet-Range-Calculator-with-Mikrotik-VLAN-Generator/refs/heads/main/subnetcalc-v7-22112024.html


## Subnet Range Calculator with VLAN Generators
This is a web-based tool designed to help network administrators calculate subnet ranges and generate VLAN configuration scripts for MikroTik devices. The tool also supports generating revert scripts to easily remove configurations, making it an invaluable resource for managing VLANs and DHCP configurations.

**Features**

1. Subnet Range Calculation:
Dynamically calculates the network address, broadcast address, usable IP range, and subnet mask based on a user-provided IP address and subnet mask.

2. VLAN Script Generator:
Automatically generates MikroTik configuration scripts for creating VLANs, assigning IP addresses, setting up DHCP pools, and blocking inter-VLAN traffic.

3. Revert Script Generator:
Provides a revert script to undo all configurations created by the VLAN generator.

4. Customisable VLAN ID Handling:
VLAN IDs are derived from the third octet of the user-provided IP address.
Option to replace VLAN ID 0 with 4094 (enabled by default via the "Replace VLAN ID 0 with 4094" checkbox).

5. DHCP Pool Range Adjustment:
Automatically starts the DHCP pool range from .2 to avoid using the reserved network address .1.

6. Prevent Overlapping Subnets:
Ensures that added subnets do not overlap with each other.

7. Inter-VLAN Blocking:
Option to block inter-VLAN traffic with a single firewall rule (enabled by default).

8. Interactive User Interface:
Clean and intuitive interface with dynamically updated dropdowns and results display.
Provides detailed network configuration summaries for each added subnet.

9. Clipboard Integration:
One-click button to copy the generated script to the clipboard.

10. Validation:
Validates IP addresses and prevents errors like overlapping subnets or invalid input formats.

### Example Outputs
**VLAN Script**
Input:
- IP Address: 192.168.88.1/20
- Replace VLAN ID 0 with 4094: Checked

Output:
`/interface vlan add name=vlan-bridge-192.168.88.1-192.168.95.254 vlan-id=88 interface=bridge
/ip address add address=192.168.88.1/20 interface=vlan-bridge-192.168.88.1-192.168.95.254
/ip pool add name=pool-vlan-bridge-192.168.88.1-192.168.95.254 ranges=192.168.88.2-192.168.95.254
/ip dhcp-server add address-pool=pool-vlan-bridge-192.168.88.1-192.168.95.254 name=dhcp-vlan-bridge-192.168.88.1-192.168.95.254 interface=vlan-bridge-192.168.88.1-192.168.95.254
/interface list member add disabled=no interface=vlan-bridge-192.168.88.1-192.168.95.254 list=LAN
/ip dhcp-server network add address=192.168.88.0/20 dns-server=192.168.88.1 gateway=192.168.88.1 netmask=20
/ip firewall address-list add address=192.168.88.0/20 disabled=no list=VLAN comment="192.168.88.0/20 VLAN address list"
/ip firewall filter add action=drop chain=forward disabled=no dst-address-list="VLAN" src-address-list="VLAN" log=no log-prefix=""
`
### Known Limitations
- The tool is designed specifically for MikroTik RouterOS and may not generate compatible scripts for other networking devices.
- Requires manual input of the initial IP address and interface details.
