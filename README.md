# Project: Network Intrusion Detection and Response

Welcome to my cybersecurity lab project focused on Network Intrusion Detection and Response. In this hands-on setup, I simulate real-world attack scenarios using virtual machines and open-source tools like Snort, Wireshark, and Metasploit. 
The goal? Detect, analyze, and respond to suspicious activities just like a professional blue team would in a real environment.

Whether you're learning network defense or building your red team toolkit, this project is designed to bridge the gap between theory and real-world action.

You can learn :  
How to deploy and configure an Intrusion Detection System (IDS) using Snort, Ways to simulate normal and malicious traffic in a virtual lab , How to analyze packets and detect anomalies using Wireshark.

Practical techniques to respond to detected intrusions.

Tools & Technologies
Tool	           Purpose
VirtualBox	     Virtual environment setup
Ubuntu	        OS for Client & IDS VMs
Kali Linux	     OS for Attacker VM (preloaded with tools)
Snort	Network    Intrusion Detection System
Wireshark	     Packet capture and analysis
Metasploit	     Attack simulation


Lab Setup

 Virtual Machines🖥️  
1. Host Machine: Controls and manages the virtual lab  

2. IDS VM: Ubuntu-based VM running Snort and Wireshark  

3. Client VM: Simulates normal network traffic  

4. Attacker VM: Kali Linux VM launching attacks  

Network Configuration  
All VMs use Host-Only Adapter to isolate them in a private test network, ensuring traffic is contained for analysis.  

Getting Started  
1. Install VMware  
Grab it from the official VMware site and install it on your host machine.  

2. Set Up VMs  
   
IDS VM (Ubuntu):   
#sudo apt-get update  
#sudo apt-get install snort wireshark  

Configure Snort (/etc/snort/snort.conf) to monitor the correct interface and IP range.

Client VM (Ubuntu)  
Basic setup, used for generating normal traffic.

Attacker VM (Kali Linux)  
Comes with Metasploit pre-installed.  

3. Network Configuration  
Ensure all VMs are connected to the same Host-Only network in VirtualBox. They should all be able to ping each other but remain isolated from your real network.

✅ Tasks & Scenarios  
**Task 1: IDS Configuration**  
Install & configure Snort on the IDS VM.  

Monitor the main interface and define basic detection rules.  

Run Snort in live alert mode:  

#sudo snort -A console -q -c /etc/snort/snort.conf -i eth0  

**Task 2: Generate Network Traffic**  

On Client VM: Run basic tools like ping, curl, iperf.  

On Attacker VM: Simulate a port scan via Metasploit:  

#msfconsole  
#use auxiliary/scanner/portscan/tcp  
#set RHOSTS <Client_VM_IP>  
#run  

**🧵 Task 3: Traffic Analysis**
Use Wireshark to capture live packets on IDS VM.

Apply filters (e.g., icmp, tcp.flags.syn==1) to identify malicious patterns.

Analyze packet data and infer attack behavior.

**🚫 Task 4: Intrusion Response**  
Identify attacker IP from Snort alerts.  

Block them using iptables:  
#sudo iptables -A INPUT -s <Attacker_IP> -j DROP  

#Update firewall rules and log the event.


Hope it Helps - Yogesh     
Cybersecurity Enthusiast | Network Defender |   
