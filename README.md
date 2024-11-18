Subnet Range Calculator and Mikrotik VLAN Script Generator

**Core Features**

**IP Address and Subnet Mask Selection:**
The app allows users to input an IP address and select a subnet mask from a dropdown.
The dropdown dynamically calculates the range of usable IP addresses and the total number of clients for each subnet mask.

**Dynamic Subnet Calculations:**
Calculates and displays the network address, broadcast address, usable range, and the number of usable clients for the entered subnet.
Prevents overlapping subnets by checking against existing configurations.

**Subnet Management:**
Add Subnet: Users can add subnets to build a network configuration.
Remove Last Subnet: Removes the last added subnet from the configuration.
Update Total Clients: Keeps track of the total number of usable clients across all subnets.

**Detailed Output for Subnet Configurations:**
Displays all added subnets with details including:
Subnet Mask (e.g., 255.255.255.0)
Network Address
Broadcast Address
Usable IP Range
Number of Usable Clients
Script Generators

**MikroTik VLAN Script Generator:**
Generates a MikroTik RouterOS script for configuring VLANs based on the added subnets.

**Script includes:**
VLAN creation with names based on the IP range (e.g., vlan-bridge-192.168.88.2-192.168.88.254).
Assigns IP addresses to VLAN interfaces.
Configures IP pools for DHCP with accurate ranges.
Adds DHCP servers for VLAN interfaces.
Adds the VLAN interfaces to the LAN list.
Configures /ip dhcp-server network entries with gateway, DNS, and netmask.
Adds /ip firewall address-list entries with proper subnet and mask (e.g., 192.168.88.0/24).
Optional: Adds an InterVLAN blocking rule to the firewall if selected.

**MikroTik Revert Script Generator:**
Generates a script to remove all previously configured VLANs and DHCP settings.

**Deletes:**
VLAN interfaces.
Assigned IP addresses.
IP pools and DHCP servers.
VLAN list memberships.
Address-list entries.
InterVLAN blocking rules (if added).

**User Experience Features**

**Dynamic Feedback:**
Displays success messages for valid actions (e.g., "Subnet added successfully").
Provides error messages for invalid actions (e.g., "The IP range overlaps with an existing subnet").

**Script Copying:**
Allows users to copy the generated script to the clipboard for easy integration into MikroTik RouterOS.

**Automatic Range Updates:**
Updates the range calculations dynamically when the IP address or subnet mask is changed.

**Technical Details**

**IP and Subnet Validation:**
Ensures valid IPv4 addresses are entered.
Calculates subnets and ranges accurately using binary arithmetic.

**VLAN Naming:**
Names VLANs, IP pools, and DHCP servers based on the usable IP range (e.g., 192.168.88.2-192.168.88.254), ensuring clarity in the configuration.
Firewall Configuration:

**Accurately adds subnets to a VLAN firewall list with correct CIDR notation (e.g., 192.168.88.0/24).**

**Customisation:**
Allows users to select VLAN interfaces (e.g., ether1, bridge, etc.).
Provides an optional toggle to block InterVLAN traffic.

**Subnet Calculation:**
Enter an IP address and update the ranges.
Select a subnet mask and add it to the configuration.

**Generate VLAN Script:**
Add all desired subnets and click "Mikrotik VLAN Script".
Copy the script or save it for use in MikroTik RouterOS.

**Generate Revert Script:**
To reset configurations on the router, click "Mikrotik Revert Script".

**This tool provides a streamlined way to calculate subnets, build VLAN configurations, and manage network scripts for MikroTik devices, ensuring accuracy and efficiency. **
