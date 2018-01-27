# DIY Linux IPV4 + IPV6 router

There were a bit too many tutorials on DIY Linux routers (ArsTechnica, Arch -, Gentoo -, Ubuntu wiki etc.), yet none on its own helped me create my own implementation. It was the joint forces of all above listed and further random forums, reddit etc.
So I thought I'd share my own configurations and applications I used to make it easier for others and to keep my notes for later use.


## Tools in use

Have these installed or get ready to replace them on your own.

* systemd
* systemctl
* netctl
* dnsmasq
* iptables
* wide-dhcpv6


## Configurations

### netctl

**working dir:** /etc/netctl

Choose a sample config from the netctl configs that best describes your WAN setup:

* PPPoE ~ wan_pppoe
* DHCP ~ wan_dhcp

and edit your WAN interface and access data.
**IMPORTANT:**  if you choose _PPPoE_ then your _WAN INTERFACE_ will be _ppp0_ from now on excluding the _wan_pppoe_ config file.


Choose one for the LAN setup too:

* Single LAN port ~ lan_single
* Multiple LAN port (dual/quadro NICs) ~ lan_bridge

**IMPORTANT:**  if you choose _BRIDGE MODE_ then your _LAN INTERFACE_ will be _br0_  (or what you name it in the config) from now on excluding the _lan_bridge_ config file.


### dnsmasq

**config:** /etc/dnsmasq.conf

Simply replace _LANIF_ with your previously configured lan interface on all 3 occurences.


### iptables

**working dir:** /etc/iptables

Replace all instances of _WANIF_ and _LANIF_ in _iptables.rules_


### wide-dhcpv6

**config:** /etc/wide-dhcpv6/dhcp6c.conf

Replace all _WANIF_ and _LANIF_ with your interfaces' names.




## Enabling services 

Use your choice of wan / lan profiles' names!

```
systemctl enable netctl
netctl enable wan_XXXX
netctl enable lan_XXXX

systemctl enable dnsmasq

systemctl enable iptables
systemctl enable ip6tables
```

## Starting services

Either simply reboot 

or 

Use your choice of wan / lan profiles' names!

```
netctl start lan_XXXX
netctl start wan_XXXX

systemctl start dnsmasq

iptables-restore < /etc/iptables/iptables.rules
ip6tables-restore < /etc/iptables/ip6tables.rules
```




