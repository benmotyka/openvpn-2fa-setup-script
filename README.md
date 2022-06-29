# General

This repository contains scripts for **installing** and **managing** OpenVPN Community with Google Authenticator 2FA functionality.

Scripts were adjusted specificaly for Linux Rocky-8-ec2-8.5*, x86_64 on AWS.

Based on article: https://perfecto25.medium.com/openvpn-community-2fa-with-google-authenticator-4f2a7cb08128 and following repo: https://github.com/perfecto25/openvpn_2fa

# Common issues

## Clients

### Windows

**Issue**: Can't import .ovpn file because of unknown dhcp-option
**Resolution**: Remove `dhcp-option DOMAIN-ROUTE .` line from client .ovpn file

**Issue**: Can't connect to server because of `TEST ROUTES: 0/0 succeeded len=-1 ret=0 a=0 u/d=down`, `Initialization Sequence Completed With Errors ( see http://openvpn.net/faq.html#dhcpclientserv )` connection logs
**Resolution**: Run below commands in cmd.exe as admin:
```
netsh winsock reset catalog
netsh int ipv4 reset reset.log
```

Add below line to client .ovpn file:
```
ip-win32 netsh
```
