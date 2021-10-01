# linux_gateway

Monitor gateway
```
# http
tcpdump -i eth1 -nn -s0 -v port 80
tcpdump -i eth1 -nn -s0 -v port 443
# ping
tcpdump -i eth1 icmp
```