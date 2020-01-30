# AP_config

This is a network config for setting up a Wifi AP under Linux 
using two wireless network (wifi) adapters. The principle can be
adapted to an arbitrary number of network adapters.

The prerequisites are Dnsmasq (for the DHCP server), Iptables 
config and Hostapd.

The source network interface is considered to be wlan0. In this 
case Hostapd is not configured to use a bridge as it is normally 
done. Instead, network traffic is rerouted from the source interface
to the destination interface (wlan1) using iptables.
DNS access is provided to OpenDNS (on port 53). DHCP access is 
on port 67 with respect to the LAN.

I have successfully used this system on a LAN as a means to 
transfer large amounts of data within a cluster of systems wirelessly. 
The performance and reliability of the system is excellent.

The network interface file creates a network on 172.24.1.1.
On the server UFW should be instructed to allow to Anywhere from 
subnet 172.24.1.48/29.

Likewise on the client(s) UFW should be allowed to Anywhere from 
172.24.1.1.
