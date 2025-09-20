# DNS-Spoofing
This lab will help you understand the working of DNS and ARP. This lab demonstrates how DNS queries can be intercepted and redirected to fake(self created) webpage.  
## Setup and Tools:
 - Kali Linux
 - Victim machine
 - Self created Isolated LAN
 - Apache2
 - Ettercap

## Notes
 - Devices to be simulated should be connected to the same network(no internet access)
 - Note the ip-address of the devices being used


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
#### Edit the etter.conf file:
```bash
sudo mousepad /etc/ettercap/etter.conf
```
#### Now inside the file :
```bash
ec_uid = 0             
ec_gid = 0
```
### 4. Apache server
```bash
sudo service apache2 start
```

### 5. Ettercap
```bash
sudo ettercap -G #(enters into the graphical mode)
```
### Configure attack:
 - Steps:
   - Sniff → Unified Sniffing → Select your network interface
   - Hosts → Scan for hosts
   - Hosts → Host list → Add Kali and Windows IPs to Target 1 and Target 2
   - Mitm → ARP poisoning → Select “Sniff remote connections”
   - Plugins → Manage plugins → Double-click dns_spoof to activate
   
