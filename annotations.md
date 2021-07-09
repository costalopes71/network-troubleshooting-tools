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

