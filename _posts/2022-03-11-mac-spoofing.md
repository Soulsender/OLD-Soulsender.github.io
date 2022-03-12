### MAC Address Spoofing and How a 16 Year Old Outplayed A System Admin

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

### Why is this Important to Know?

Well, every device that connects to a WiFi network, via wireless or ethernet, will give that network it's MAC address. This way, the network knows who to give requested traffic to. There are ways to SPOOF MAC addresses however, and that's the important part of this story. MAC spoofing is possible on pretty much all operating systems, even iPhones have a built in way to use a seperate MAC address than the real one. This is important to note.
<br /><br />
To be clear - I had no ill-intent during my discovery of this process. It's not illegal, and is perfectly fine to do. After my discovery of my laptop's MAC address being blocked, I had the idea to generate a new, random address for my laptop. Using a very simple Linux command-line program called [`macchanger`](https://github.com/alobbs/macchanger), you can generate and use random MAC addresses. 
<br /><br />
So I used this program to generate a new and random address for my device. It's very easy to do:
```
sudo macchanger -r wlp59s0
```
`wlp59s0` is the name of my wireless card. Usually this can be listed as `wlan0` or something else. You can look this up via `iwconfig`. Using this randomly-generated MAC address worked for a full 15 minutes! ...and then I got blocked again. There was some sysadmin somewhere that was seeing me connect to this network, and probably thought it was a little suspisous that they were using a Linux distrobution for one of two reasons. 1) No normal person uses Linux, especially not a student at a high-school. 2) Linux is very commonly used for hacking. I can't really blame them for wanting to try to block me ¯|_(ツ)_/¯.

### What Now?

Hm. Well random MAC addresses didn't work, and my static one was blocked. After this, I tried using MAC addresses from different vendors, such as Apple and Cisco, but no bueno. Remember that thing earlier how iPhones have a built-in MAC changer thing? I thought about this, and I realised that my phone hadn't been kicked off the network. This meant two things. 
<br /><br />
1) They only saw my device, which means they don't know who's actually behind the strange Linux device on their network. When you join the WiFi network at my school, you are required to put in you student credentials. This means they can directly link activity on a network to a certain student depending on who is signed in as that user on that device. 
<br /><br />
2) I could *steal* the MAC address of my phone and use that to get internet, because it was already registered on the network. 
<br /><br />
After copying and inputing my phone's MAC address into my laptop via
```
sudo macchanger -m (the phone's mac address) wlp59s0
```
I restarted the network manager daemon, and BOOM. I had internet again. Because my iPhone was already registered on the network BEFORE I started messing with my laptop's MAC, it would not look suspicious at all - they would have no way to know the owner of the MAC address had changed. To the network, it was my phone - when in reality, it was my laptop.

### Conclusion

I'll do this later lol
