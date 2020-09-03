Configure Networking on Ubuntu
During the installation of Ubuntu on your server an IP address was most likely obtained automatically. This dynamic IP address assignment will need to be changed to a static IP address. This section will cover the simple network configuration changes needed to set a static IP network address for your server. For this section, the directions assume the configuration is for a node with only one interface (eth0) after a default installation.

Note
These instructions assume that the reader is familiar with opening, editing and saving files at the command line. Please consult your OS documentation if you need assistance with these tasks.

Most Linux systems have a few commands that can be used to find out what the current network configuration is, for example:

### ifconfig -a
You can also use variations of the ip command:

### ip addr
Basic network configuration and hostname on a Ubuntu system are stored in several files which must be edited to create a working configuration:

### /etc/network/interfaces describes the network interfaces
### /etc/hostname configures the nameserver credentials
### /etc/hosts resolves IP addresses to hostnames
Once the new configuration is saved the interface must be restarted.

Changing Network Configuration
Below is an example of a static IP configuration on a system with only one Ethernet interface (eth0) and 10.0.0.41/24 for the IP address. Opening the /etc/network/interfaces file will produce:

 This file describes the network interfaces available on your system
 and how to activate them. For more information, see interfaces(5).

 The loopback network interface
auto lo
iface lo inet loopback
## 
 The primary network interface
## auto eth0
## iface eth0 inet static
    address 10.0.0.41
    netmask 255.255.255.0
    network 10.0.0.0
    broadcast 10.0.0.255
    gateway 10.0.0.1
    dns-nameservers 10.0.0.1 8.8.8.8
    dns-domain acme.com
    dns-search acme.com
Open your /etc/network/interfaces file, locate the:
"iface eth0..." line and change dynamic to static
address line and change the address to the static IP address
netmask line and change the address to the correct subnet mask
gateway line and change the address to the correct gateway address
dns-nameservers line and change (or add) the nameserver information
If you aren't certain which IP address, subnet mask, gateway or dns-nameservers you need, please consult with your network administrator for the correct information.

When you are happy with your configuration restart the interface with the command below. If you are connected using SSH you will lose your connection, re-connect using the new IP address:

ifdown eth0; ifup eth0
Changing the Hostname
To change the hostname to your preferred node name (example: prodnode01), you have to edit the /etc/hostname file:

prodnode01
Adding the FQDN (Hostname)
To ensure your server traffic will be routing correctly add the server's Fully Qualified Domain Name (FQDN) and IP address to the hosts file. Open the /etc/hosts file and add a line with the static IP address and the FQDN, similar to the example shown below:

192.168.0.0 prodnode01.acme.com
With all your files edited and saved, you should reboot so the new name and configuration will be used.

Reboot the system and then use ifconfig or ipaddr to confirm that your new configuration is available. You can also use hostname -f to verify the hostname change,

Configure Networking on CentOS / Red Hat
During the installation of CentOS/Red Hat on your server an IP address was most likely obtained automatically. This dynamic IP address assignment will need to be changed to a static IP address. This section will cover the simple network configuration changes needed to set a static IP network address for your server. For this section, the directions assume the configuration is for a node with only one interface (eth0) after a default installation.

Note
These instructions assume that the reader is familiar with opening, editing and saving files at the command line. Please consult your OS documentation if you need assistance with these tasks.

Most Linux systems have a few commands that can be used to find out what the current network configuration is, for example:

ifconfig -a
You can also use variations of the ip command:

ip addr
Basic network configuration and hostname on a CentOS/Red Hat system are stored in several files which must be edited to create a working configuration:

/etc/sysconfig/network specifies routing and host information for all interfaces
/etc/sysconfig/network-scripts/ifcfg-ethX contains the configuration scripts for each network interface
/etc/resolv.conf configures the nameserver credentials
/etc/hosts resolves IP addresses to hostnames
Changing Network Configuration
Name server configuration is in /etc/resolv.conf:

search acme.com
nameserver 10.0.0.1
nameserver 8.8.8.8
Open your /etc/resolv.conf file, locate the:
first nameserver line and change the nameserver information
second nameserver line and change (or add) the nameserver information
If you aren't certain which nameservers you need, please consult with your network administrator for the correct information.

Below is an example of a static IP configuration on a system with only one Ethernet interface (eth0) and 10.0.0.41/24 for the IP address. Opening the /etc/sysconfig/network-scripts/ifcfg-eth0 file will produce:

DEVICE="eth0"
BOOTPROTO="none"
ONBOOT="yes"
TYPE="Ethernet"
IPADDR=10.0.0.42
NETMASK=255.255.255.0
BROADCAST=10.0.0.255
GATEWAY=10.0.0.1
Open your /etc/network/interfaces file, locate the:
BOOTPROTO line and change dhcp to none.
IPADDR line and change the address to the static IP address
NETMASK line and change the address to the correct subnet mask
GATEWAY line and change the address to the correct gateway address
If you aren't certain which IP address, subnet mask or gateway you need, please consult with your network administrator for the correct information.

Changing the Hostname
For a node called prodnode02.acme.com the content of the /etc/sysconfig/network file would look like this:

NETWORKING=yes
HOSTNAME=prodnode02.acme.com
Open your /etc/sysconfig/network file, locate the HOSTNAME line and change the hostname to your preferred node name.

Adding the FQDN (Hostname)
To ensure your hostname and IP address are routing correctly the Fully Qualified Domain Name (FQDN) and IP address should be added to the hosts file. Open the /etc/hosts file:

192.168.0.0 prodnode01.acme.com
With all your files edited and saved, you should reboot so the new name and configuration will be used.
