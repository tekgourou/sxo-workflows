# Setup - IP / FQDN Block list - ObjectGroup and FW rules

This workflow create Meraki IP and FQDN Policy Object Group and FW rules for a given Organization. This is the initial setup for the workflow “Meraki - MX - add IP / FQDN to blocklist”

## Requirements
The following system atomics are used by this workflow:
    * Meraki - Get Networks by Organization
    * Meraki - Get Organizations
    * Meraki - Network - MX - Get L3 Outbound Firewall Rule
    * Meraki - Network - MX - Update L3 Outbound Firewall Rules
* 		The following atomic actions must be imported before you can import this workflow:
    * Meraki - Get Policy Objects Groups list (available from my atomics gethub repository)
    * Meraki - Create Policy Objects Group (available from my atomics gethub repository)
    * Meraki - Create Policy Object (available from my atomics gethub repository)
    * Meraki - Get Syslog Servers for a NetworkID (available from my atomics gethub repository)
* Cisco Meraki MX appliance(s)
