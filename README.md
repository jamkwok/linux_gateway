# linux_gateway

## Instructions
Gateway Box
```shell
cd gateway
vagrant up
vagrant ssh
sudo su -
# change default route to be that of eth1 via public network (your own network and not internal vagrant network)
route add default gw 192.168.0.1 eth1 # assumes your public internet rotue is 192.168.0.1
route del default gw 10.0.2.2 # remove vagrant default route

```
Device Box (will use Gateway Box for internet routing)
```shell
cd device
vagrant up
sudo su -
route add default gw 192.168.0.27 eth1 #In this scenario device had 192.168.0.28 and gateway .27
route del default gw 10.0.2.2

```

Monitor gateway
```
# http
tcpdump -i eth1 -nn -s0 -v port 80
tcpdump -i eth1 -nn -s0 -v port 443
# ping
tcpdump -i eth1 icmp
# ping but data frame
tcpdump -i eth1 icmp -e
# zerotier 
tcpdump -i eth1 -nn -s0 -v port 9993
```