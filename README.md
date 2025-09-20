# DNS-Spoofing
This lab will help you understand the working of DNS and ARP. This lab demonstrates how DNS queries can be intercepted and redirected to fake(self created) webpage.  
## Setup and Tools:
 - Kali Linux
 - Victim machine
 - Self created Isolated LAN
 - Apache2
 - Ettercap

## Methodology:
### 1. Find the ip_address of the host and victim machine
```bash
ifconfig #(For Linux)
```
```bash
ipcofig #(For Windows)
```
### 2. IP-Forwarding:  
 ```bash
sudo sysctl -w net.ipv4.ip_forward=1
```
### 3.Add ip-addresses to the etter.dns file
  ```bash
 sudo mousepad /etc/ettercap/etter.dns 
  ``` 
##### Now inside the file, Add:
```bash
 example.com A <ip-address> # ip-address of the host machine
``` 
### 3.1 Edit the etter.conf file:
```bash
sudo mousepad /etc/ettercap/etter.conf
```
#### Now inside the file :
```bash
ec_uid = 0             
ec_gid = 0
```
