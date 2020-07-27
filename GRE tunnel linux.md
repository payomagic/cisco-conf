###	GRE Tunnel - Linux

```
iptunnel add gre1 mode gre local 1.2.3.4 remote 4.3.2.1_IP ttl 255
ip addr add 192.168.168.1/30 dev gre1
ip link set gre1 up	
```
