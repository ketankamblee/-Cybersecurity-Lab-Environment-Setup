# -Cybersecurity-Lab-Environment-Setup
Isolated Virtual Lab built with Virtualbox and Kali Linux for cyber security and penetration testing practice.


# 📌 Project Overview
This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

# 🎯 Objectives
The main objectives of this project are to:
1. Install and configure VirtualBox.
2. Install/import Kali Linux as a virtual machine.
3. Create a private NAT Network for the cybersecurity lab.
4. Configure network connectivity for Kali Linux.
5. Assign a consistent IP address to the Kali VM.
6. Verify network connectivity and DNS resolution.
7. Take a clean VM snapshot for recovery.
8. Document the complete setup process.
9. Prepare the environment for future cybersecurity projects

# 🛡️ Purpose of the Lab
The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.
1. It can be used for activities such as:
1. Network reconnaissance
1. Port scanning
1. Vulnerability assessment
1. Packet analysis
1. Web security testing
1. Security-tool experimentation

# Lab Features

| 🧩 Component | ⚙️ Configuration |
| :--- | :--- |
|🖥️ Host OS | Windows 11 |
|🧠 Host RAM | 16 GB |
|⚡ Processor | Ryzen 5 |
|🧰 Hypervisor | VirtualBox 7.2 |
|🐉 Security OS |Kali Linux 2026.2|
|🧠 Kali RAM | 2048 MB |
|🌐 Virtual Network |NAT Network|
| 📡 Network Address |10.0.0.0/24 |
|🐧 Kali IP Address | 10.0.0.2/24 |
|🚪 Default Gateway | 10.0.0.1 |
| 🌍 DNS Server | 8.8.8.8 |

# Lab Setup Procedure
# Step 1. install 7-Zip
7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a .7z archive.

Tool: 7-Zip

# Step 2. Install VirtualBox
VirtualBox was installed as the hypervisor.

# Step 3. Create the NAT Network
A dedicated NAT Network was created in VirtualBox.

Configuration: Network Name: NatNetwork IPv4 Prefix: 10.0.0.0/24 DHCP: Enabled IPv6: Disabled
<img width="1852" height="895" alt="Screenshot 2026-09-07 135240" src="https://github.com/user-attachments/assets/7f607ccc-8386-4761-8f97-408b872c164f" />

A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

# Step 4. Import Kali Linux
The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

Adapter 1

Attached to: NAT Network

Network:     NatNetwork

Adapter Type: Intel PRO/1000 MT Desktop

The VM was allocated :

RAM: 2048 MB
<img width="1517" height="716" alt="Screenshot 2026-09-07 143043" src="https://github.com/user-attachments/assets/84b3b1ed-9728-4222-9767-a76360f50ae7" />
# Step 5. Configure the Kali Linux Network
The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

IP Address: 10.0.0.2

Subnet Mask: 255.255.255.0

Gateway: 10.0.0.1

DNS: 8.8.8.8

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.
<img width="1917" height="978" alt="Screenshot 2026-09-07 143207" src="https://github.com/user-attachments/assets/03327ab0-5589-4ead-93f8-0ec5e4ea52f1" />
# Step 6. Create a Clean VM Snapshot
After completing the initial configuration, a VirtualBox snapshot was created.
Example snapshot name:

Newly Installed Kali Linux

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.
# Lab Verification 

| ✅ Test | 🧾 Command | 🎯 Expected Result |
| :--- | :--- | :--- |
| 🌐 Check IP address | ip a | 	Correct Kali IP displayed |
| 📡 Test gateway | 	ping 10.0.0.1 | Successful replies |
| 🌍 Test Internet connectivity | ping 8.8.8.8 | 	Successful replies |
| 🔎 Test DNS resolution | 	nslookup networkwalks.com | 	Domain resolves |
| 🧰 Verify Nmap | 	nmap --version | 	Nmap version displayed |
| 🔄 Verify snapshot | 	Restore snapshot and run ip a | Baseline configuration restored |

# Example result 
IP Address: 
10.0.0.2/24

Gateway: 
10.0.0.1

DNS: 
8.8.8.8

# Problems Encountered & Sokutions
# Problem 1. Internet Connectivity After Static IP configuration
After manually configuring the IPv4 settings, Internet connectivity may fail depending on the Kali/NetworkManager configuration.

One workaround used during this lab was:

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0

The network connection was then restarted/rebooted and connectivity was tested again.

# What I Learned
Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.


The most important concepts I learned include:

1. NAT vs NAT Network

A standard NAT configuration and a NAT Network serve different purposes.


A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.


This makes it useful for building a multi-machine cybersecurity laboratory.


2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.


3. Static IP Configuration

I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.


4. VM Snapshots

I learned that a clean snapshot should be created before performing risky or experimental activities.


This provides a known-good recovery point for future cybersecurity exercises.


5. Documentation
6. 
I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

# Security & Ethical Use
This Lab is strictly for education purpose only.

# Tools & Resources
1. 7-Zip: https://7-zip.org/download.html

2. VirtualBox: https://virtualbox.org/wiki/Downloads

3. Kali Linux: https://kali.org/get-kali
# Author
Ketan Kamble 

Cyber Security Student.

LinkedIn: https://www.linkedin.com/in/ketan-kamble-237a63316/

# Project Information
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub
