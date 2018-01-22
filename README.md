# diyrouter
Router implementation for home

## What works
* PPPoE connects fine. On the router itself there is a perfectly fine and 
working connection as far as I can tell (CLI only, but everything pings,
curl loads, speedtest-cli runs fine)
* DHCP serves addresses on the LAN, ssh works to / from the router
* NAT / Masquerading works. Clients reach the internet (well, some of it)


## What doesn't work
* Clients don't reach some / most of the internet. Google.com, Reddit.com works.
Some pages, like a local forum (prohardver.hu) load incredibly slowly and sketchy
Some pages won't load at all (speedtest.net)
apt install xyz hangs on "waiting for headers 0%"


