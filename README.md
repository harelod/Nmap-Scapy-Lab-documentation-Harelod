# Nmap-Scapy-Lab-documentation-Harelod
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
  

  


  

