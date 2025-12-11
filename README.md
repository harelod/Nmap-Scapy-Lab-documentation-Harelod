# Nmap-Scapy-Lab-Documentation-Harelod
This focuses on the utilization of Nmap and Scapy tools during our instructor lead classes at ParoCyber.

## 1. Objective of Lab
The main purpose of this lab was to re-run a practical training on the use of Nmap and Scapy tools on Ethical Hacker Kali Linux to asertain the following; 
- Host Discovery
- Open ports
- OS Fingerprinting
- Perform aggresive service scan on specific ports (Port 21)
- Determine file transfer protocol version and number of shared files on port 21 & port 445 using smb scanning and enumeration
- Log in anonymously to a user account after performing smb scanning
- Determine Physical Ethernet Network card and Virtual network bridge IP addresses
- To see the communication route on Virtual Machine whiles visiting websites
- Determine DNS Server used
- Crafting of Packets
- sniffing of packets using Scapy
- Preview of TCP, DNS and ICMP within captured packets

All the above was to help a student or learner  gain basic skills on how to perform active reconnaissance, enumeration, sniffing and analysis of captured packets.

## 2. Setup Environment
 - Vitual Machine:
 - Operating System:
 - Tools: Nmap & Scapy
 - Network Range: 10.6.6.0/24
 - Target Host: 10.6.6.23
 - Network Interface :Eth0/bridge vitual network
 - Lab Guide: Parocyber ethical hacking training

# (A) Nmap Results & Docummentations
## 1. Host Discovery
### Command: ``` Sudo nmap -sn 10.6.6.0/24 ``` 
### Purpose: To identify active hosts on the network
<img width="814" height="449" alt="image" src="https://github.com/user-attachments/assets/56ca4d10-bd02-4a87-bc08-cd59e1e60a69" />

### Seven (7) Hosts were discovered:

- 10.6.6.1
-  webgoat.vm (10.6.6.11)
-  juice-shop.vm (10.6.6.12)
-  dvwa.vm (10.6.6.13)
-  mutillidae.vm (10.6.6.14)
-  gravemind.vm (10.6.6.23)
-  10.6.6.100


  ## 2. Open Ports & OS Fingerprinting
  ### Command: ``` sudo nmap -O 10.6.6.23 ``` 
  ### Purpose: To identify open ports, Operating system and version
  <img width="940" height="489" alt="image" src="https://github.com/user-attachments/assets/5b4dd0e4-efc2-487b-8766-fb8428f22a40" />

  ### (i) Six (6) open ports were identified (Port 21, 22, 53, 80, 139 & 445)
  ### (ii) OS Fingerprinting: 
  - Device type: general purpose 
  - Running: Linux 4.X|5.X
  - OS details: Linux 4.15 - 5.8

## 3. Aggressive Service Scan on selected Port 21
### Command: ``` nmap -p21 -sV -A -T24 10.6.6.23 ``` 
  ### Purpose: To perform aggressive service scan on the selected port, to identify and gather information on file transfer protocol (FTP) and version
  <img width="940" height="596" alt="image" src="https://github.com/user-attachments/assets/314dce16-8460-45a0-9a83-c88038a2cead" />

  ### Four (4) files were identified on Very Secure File Transfer Protocol (VSFTP): (file1. txt, file2.txt, file3.txt & supersecretfile.txt) with a vsftP version 3.0.3

  Note: vsftp allows users to download and upload files over FTP which supports both anonymous and authenticated access.
  
  ## 4. Aggressive Services Scan - On more than one (1) Ports
  ### Command: ``` nmap -A -p 139,445 10.6.6.23 ``` 
  ### Purpose: To identify target operating system, version services running on open ports and scripts information.
  <img width="940" height="694" alt="image" src="https://github.com/user-attachments/assets/7346187d-d99b-4e7e-a4c6-9bc441c0d114" />

  ### The above is used to obtain detailed information about your target machine during Pentesting, Reconnaissance and network troubleshooting. Since is easy to be dectected, it is advice not be used on live or real network without permission.

  
## 5. Aggressive Services Scan
### Command: ``` nmap --script smb-enum-shares.nse -p445 10.6.6.23 ```
### Purpose: To list SMB share (all shared folders) on an SMB server of a target machine, ascertain its accessibility (anonymous/authenticated access,read/write)
<img width="922" height="862" alt="image" src="https://github.com/user-attachments/assets/b17e17a8-c3ac-4251-87e0-bc8224ebf7d0" />

### Three (3) folders can been seen as shared on the target machine which can be accessed anonymously

## 6. Anonymous Login
### Command: ``` smbclient //10.6.6.23/print$ -N ```
### Purpose: To have anonymous access to print folder on our target machine (10.6.6.23)
<img width="940" height="634" alt="image" src="https://github.com/user-attachments/assets/321889f7-6d64-4920-b40a-ce293a2999a5" />

  ### NB: After logining in anonymously the help is used to detail all functions that can be performed and quit is used to close the script.

  ## 7. Physical Ethernet Network card and Virtual network bridge
  ### Command: ``` ifconfig ```
### Purpose: To identify IP address and broadcast on a physical ethernet network (etho) or Virtual network bridge (br-internal) 
<img width="940" height="641" alt="image" src="https://github.com/user-attachments/assets/d439238b-4689-4eb7-90e6-77fed15837e6" />
<img width="940" height="777" alt="image" src="https://github.com/user-attachments/assets/00efd9d7-5867-4e00-8b6e-b9d91e8547a9" />

 ## 8. Route Table
  ### Command: ``` ip route ```
### Purpose: To view and manage the routing table on a system
<img width="938" height="231" alt="image" src="https://github.com/user-attachments/assets/5fda646a-0e17-4450-bcd5-cc000b75d202" />

### NB: It shows where a system sends network trafics or packets to.

## 9. Domain Name System - DNS
  ### Command: ``` cat /etc/resolv.conf ```
### Purpose: To show the DNS Servers used on a system
<img width="466" height="132" alt="image" src="https://github.com/user-attachments/assets/8622e583-3c61-4af7-a5cf-4443f3021f5e" />

### From the above the server used is 10.0.2.3

## 9. Packet Capture using TCPDUMP and Save
  ### Command: ``` sudo tcpdump -i eth0 -s 0 -w harelod.pcap ```
### Purpose: To capture all network trafic from a specific interface and save to a file name.
<img width="940" height="158" alt="image" src="https://github.com/user-attachments/assets/9815cd93-d1df-4922-8baf-5d9566ce3520" />

### Nb: Ctrl+ c  is used to stop packet capture
- tcpdump is used to capture traffice, -i eth0 is used to specify the network interface to capture from, -s 0 to conduct full packet capture, -w is used to save the packets into file instead of showing them on screen and harelod.pcap is the packet file name.

## 10. Saved Packet
### Command: ``` ls harelod.pcap ```
### Purpose: To verify if captured packet is saved to the specific file name
<img width="320" height="102" alt="image" src="https://github.com/user-attachments/assets/3207108d-0396-4d9f-a331-a9f85b6e36af" />

## 10. Alternate Packet Capture- Wireshark
### Command: ``` wireshark ```
### Purpose: To use wireshark to load saved packet in aid of packet analysis (tcp, icmp & DNS)
<img width="289" height="63" alt="image" src="https://github.com/user-attachments/assets/1faa479e-299b-4027-bd20-c93b5c3928ee" />
<img width="848" height="700" alt="image" src="https://github.com/user-attachments/assets/11a8b562-c185-41af-8a24-319d9bb7fbe3" />
<img width="852" height="702" alt="image" src="https://github.com/user-attachments/assets/a505f970-8fb7-4302-9e2b-4d9b510454b0" />
<img width="858" height="702" alt="image" src="https://github.com/user-attachments/assets/51441ee5-fcd3-4aee-ad7c-30c673dcd2cd" />
<img width="1920" height="898" alt="image" src="https://github.com/user-attachments/assets/c82f5723-d35f-4ed0-84d8-70840adcffac" />
<img width="1913" height="894" alt="image" src="https://github.com/user-attachments/assets/5f4f306e-262a-4877-b214-f270fee8bd02" />
<img width="1913" height="899" alt="image" src="https://github.com/user-attachments/assets/23a3f4b0-1e1b-4620-8211-08f8daba08d9" /> 

### The above shows PACKETS FILTRED BY tcp, DNS & ICMP


# (B) Scapy Results & Docummentations
## 1. Root Privilege
### 1st Command: ``` sudo su  ``` 
### Purpose: To gain privilege to access network in order to send, read and manipulate packets
<img width="750" height="105" alt="image" src="https://github.com/user-attachments/assets/b73e5b30-ceab-4e7a-baca-0acec630f5f8" />

## 2. Initiate Scapy
### 1st Command: ``` scapy  ``` 
### Purpose: To start scapy tool
<img width="1055" height="466" alt="image" src="https://github.com/user-attachments/assets/7e82b866-815c-48c0-b0a9-0ff9ff2b69e4" />

