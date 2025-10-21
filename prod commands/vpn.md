route add 10.0.44.0 mask 255.255.255.0 192.168.62.1 -p
route add 192.168.9.0 mask 255.255.255.0 192.168.62.1 metric 1 if 44 -p
route add 192.168.9.233 mask 255.255.255.255 192.168.62.1 metric 1 if 44 -p
route add 10.0.44.238 mask 255.255.255.255 192.168.62.1 metric 1 if 44 -p
route add 172.20.0.0 mask 255.255.255.0 192.168.62.1 metric 1 if 44
route add 192.168.9.0 mask 255.255.255.0 192.168.62.1 metric 1 if 44 -p







ssh server
route add 172.20.0.197 mask 255.255.255.255 192.168.62.1
route add 172.20.0.0 mask 255.255.0.0 192.168.62.1
route add 192.168.9.0 mask 255.255.255.0 192.168.62.1