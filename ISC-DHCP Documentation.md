## ISC DHCP

[ISC DHCP](https://www.isc.org/dhcp/) was a complete open source solution for implementing DHCP servers, relay agents, and clients.

## Installation

Before we install ISC-DHCP Server on our debian machine let us first perform an update:
```
apt update -y
```
<br>

Let us then edit the network inteface that we will be using:
```
nano /etc/default/isc-dhcp-server
```
<br>

Let us then paste the following:
```
INTERFACESv4="eth0"
```
<br>

One done, Let's install ISC DHCP on our machine:
```
apt install isc-dhcp-server -y
```
<br>

## Configuration

Once it is downloaded, let us configure by editting the ```dhcpd.conf``` located on the ```/etc/dhcp```:
```
nano /etc/dhcp/dhcpd.conf
```
<br>

We will then paste the following:
```
default-lease-time 600;
    
subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.2 192.168.1.254;
 option routers 192.168.1.1;
```
<br>

**Explaination:**

* ```default-lease-time``` Refers to the lease time if the IP Address. In this case, it is set to ```6000``` (10 minutes).
* ```subnet``` Refers to the network that we will be using.
* ``` netmask``` Is like a filter that helps define the boundaries of a network. In this case, we will be using ```255.255.255.0``` or ```/24``` which has an available of 254 IP addresses.
* ```range``` refers to the range of IP addresses that will be allocating.
* ```option routers``` refers to the default gateway. In this case, is set to ```192.168.1.1```.
<br>

Once done, Let us restart the dhcpd service:
```
systemctl restart isc-dhcp-server
```
<br>




