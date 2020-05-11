# Aruba Instant Python API Wrapper

This module provides a Python 3 interface for the Aruba Instant 8.6 REST API.



For full documentation, see [here](https://support.hpe.com/hpesc/public/docDisplay?docId=a00092466en_us).

The REST API is divided into three secions.  **Monitoring**, **Action**, and **Configuration**.

## Monitoring
The monitoring endpoints of the API does is used for, obviously, monitoring.  It is used to gather state, statistics, and logs from master, slave, or standalone Instant APs.

The architecture of this portion of the API is very similar to the cli output of "show" commands.  The currently supported commands are ```show clients``` and ```show aps```.  More will be added shortly.

    NOTE: The response from the API is currently unstructred text and requires parsing with RegEx.  
    This lends itself to breaking easily between versions.  My current testing has been against 8.6.

## Action
The action endpoints are used for configuring AP specific settings.  See below for supported endpoints.

Endpoint | Method | Description
--- | --- | ---
Hostname | hostname() | Set the hostname of a specific IAP.
Swarm Mode | swarm() | Set an AP to be standalone or part of a swarm cluster.
Static Channel and Power | channel() | Set the tx channel and power of the radios of a specific IAP.
Zone | zone() | Set the zone of a specific IAP.
Antenna Gain | antenna_gain() | Set the specific antenna gain when external antennas are used.
Enable and Disable Radios | radio_state() | Enable or disable a radio in an AP.
Generic Show Command | show_cmd() | Returns unstructured output text from any "show" command provided.

## Configuration
Configuration endpoints are used to configure an Instant Virtual Controller.  See table below for supported endpoints.

    Note: Due to the complexity of the profiles created using these endpoints, 
    all Configuration methods require a json file as an argument.

    There are examples in the "templates" directory.  
    These example templates were taken directly from the 
    Aruba Instant REST API document referenced above.

Endpoint | Method | Description
---|---|---
VC Country Code | vc_country_code() | Set the virtual controller country code.
VC IP address | vc_ip() | Set the IP of the virtual controller.
NTP Server | ntp() | Set the NTP server of the virtual controller.
Syslocation | syslocation() | Set the syslocation of the virtual controller.
Organization | organization() | Set the virtual controller organization.
Syslog Level | syslog_level() | Set the syslog level for the virtual controller.
Syslog Server | syslog_server() | Set the destination IP for syslog traffic from the virtual controller.
dot11g Radio Profile | radio_11g() | Configure a radio profile for the 2.4GHz antenna.
dot11a Radio Profile | radio_11a() | Configure a radio profile for the 5GHz antenna.
ARM | arm() | Configure an ARM profile for use by the Instant cluster.
SSID Profile | ssid() | Configure an SSID profile for use by the Instant cluster.
RF Band | rf_band() | Configure an RF Band (2.4, 5, all) profile for use by the Instant cluster.
Authentication Server Profile | auth_server() | Configure an authentication server (RADIUS) for the virtual controller.
ACL Profile | acl() | Configure an ACL profile for use by the Intant cluster.
External Captive Portal | ext_captive_portal() | Configure an External Captive Portal profile for use by the Instant cluster.
IDS | ids() | Configure an IDS profile for use by the Instant cluster.
Software Upgrade | os_upgrade() | Initiate an OS Upgrade of the Instant cluster.
Time Zone | clock() | Set clock and timezone of the virtual controller.
AP Reboot | ap_reboot() | Initiate a reboot of a single or all APs in the Instant cluster.
Wired Port Profile | wired_port() | Configure a wired port profile for use by the Instant cluster.
Wired Profile Map | wired_profile_map() | Configure a wired profile to port mapping for use by the Instant cluster.
Management User | mgmt_user() | onfigure management users on the virtual controller.