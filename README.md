# DIY Linux IPV4 + IPV6 router

There were a bit too many tutorials on DIY Linux routers (ArsTechnica, Arch -, Gentoo -, Ubuntu wiki etc.), yet none on its own helped me create my own implementation. It was the joint forces of all above listed and further random forums, reddit etc.
So I thought I'd share my own configurations and applications I used.

### Tools in use

Have these installed or get ready to replace them on your own.

* systemd
* systemctl
* netctl
* dnsmasq
* iptables
* wide-dhcpv6


### Personalisation

Just inspect ALL configurations and edit accordingly to your setup. After which you can just enable all:

```
systemctl enable netctl
netctl enable pppoe
netctl enable lanprof

systemctl enable dnsmasq

systemctl enable iptables
systemctl enable ip6tables
```



