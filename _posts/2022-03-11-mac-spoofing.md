### MAC Address Spoofing and the ARP Protocol

Today, as per usual, I was at school. I was working normally when all of a sudden - internet was cut to my laptop. I run Linux as my desktop, and sometimes the network-manager does not initialize on boot. This is usually fine, I just need to restart the network daemon. This is a pretty simple and self-explanatory command:
```
sudo service network-manager restart
```
This command will restart the network manager daemon service run by systemd. I tried this (spolier alert: it didn't work). 
<br /><br />
The next thing I tried was flushing the DNS cache. This process is also very simple:
```
sudo systemd-resolve --flush-caches
sudo resolvectl flush-caches
```
This didn't work either, and I tried one more thing. The MAC Address.

### What is a MAC Address?

MAC stands for Media Access Control address. Every device has a MAC address. A MAC address is used sort of like an IP address, but only on a local area network (LAN). A router on a network delivers traffic to a device with the correct MAC address. This is done through the ARP (Address Resolution Protocol) which you can sort of think of like the DNS for MAC addresses. A MAC address consists of six sets of two numbers or letters, seperated by a colon. Example: `9C:6A:BD:07:B7:92`
<br /><br />
Unlike IP addresses, MAC addresses are static and do not change (there are some exceptions but for the most part, they stay the same on all networks). A MAC address will have infomation about the vendor of the device. For instance, you might be able to tell that a device is an Apple or Dell product based on the MAC address.
