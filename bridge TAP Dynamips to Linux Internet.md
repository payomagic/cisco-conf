	==========================================
	 ### Bridge TAP Dynamips to Linux Internet
	==========================================
	
	Create a TAp device (user running dynamips):
	```
	tunctl -u username
	```
	assign an ip address to the tap0 interface 
  ```
  ifconfig tap0 10.123.1.1 netmask 255.255.255.0 up
  ```
  enable the routing on the machine 
  ```
  echo 1 > /proc/sys/net/ipv4/ip_forward
  ```
  enabled masquerading on packets exiting the eth0 interface:
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i tap0 -j ACCEPT
iptables -A INPUT -i tap0 -j ACCEPT
```
assign an IP address on the same subnet to router interface attached to the cloud symbol, 
and define a default route going to the tap0 ip address
