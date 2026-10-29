# Networkwalks-BO84E-week-01-Cybersecurity-Lab-Environment-Setup-
Cyber security lab set up 
Cybersecurity Lab Environment Setup
​Building an isolated virtual lab for penetration testing and ethical hacking practice
​Host OS: Windows 10
​Host RAM: 8 GB
​Processor: Intel Core i7
​Hypervisor: VirtualBox 7.2
​Security OS: Kali Linux 2026.2
​Virtual Network: NAT Network
​Kali IP Address: 10.0.0.2/24
​📌 Project Overview
​This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.
​The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and neatly.
​The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.
​🎯 Objectives
​The main objectives of this project are to:
​Install and configure VirtualBox
​Install/import Kali Linux as a virtual machine
​Create a private NAT Network for the cybersecurity lab
​Configure network connectivity for Kali Linux
​Assign a consistent IP address to the Kali VM
​Verify network connectivity and DNS resolution
​Take a clean VM snapshot for recovery
​Document the complete setup process
​Prepare the environment for future cybersecurity projects
​🧪 Purpose of the Labu
​The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.
​It can be used for activities such as:
​Network reconnaissance
​Port scanning
​Vulnerability assessment
​Packet analysis
​Web security testing
​Exploitation practice
​Security-tool experimentation
​⚠️ Important: This laboratory must be used only for systems that you own or have explicit permission to test. Do not use the lab tools to attack unauthorized systems.
​🏗️ Lab Architecture
​(Diagram showing Host OS Windows 10, 8 GB RAM, Intel Core i7, VirtualBox 7.2 hypervisor running Kali Linux 2026.2 with 2048 MB RAM, connected via a NAT Network 10.0.0.0/24, with Kali IP 10.0.0.2 and Default Gateway 10.0.0.1)
​Additional target machines can be added to the same virtual network in future projects.
​💻 Lab Configuration

Component
Configuration
Host OS
Windows 10
Host RAM
8 GB
Processor
Intel Core i7
Hypervisor
VirtualBox 7.2
Security OS
Kali Linux 2026.2
Kali RAM
2048 MB
Virtual Network
NAT Network
Kali IP Address
10.0.0.2/24
Default Gateway
10.0.0.1
DNS Server
8.8.8.8
Future VM Range
10.0.0.3–10.0.0.99

🛠️ Lab Setup Procedure
​Step 1. Install 7-Zip
​7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a .7z archive.
​Tool: 7-Zip
​Step 2. Install VirtualBox
​VirtualBox was installed as the hypervisor.
​Step 3. Create the NAT Network
​A dedicated NAT Network was created in VirtualBox.
​Configuration Name: NatNetwork · IPv4 Prefix: 10.0.0.0/24 · DHCP: Enabled · IPv6: Disabled
​A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.
This will allow future attackers and target VMs to communicate within the lab.
​Step 4. Import Kali Linux
​The Kali Linux virtual machine was downloaded from the official Kali website and imported into VirtualBox.
​The VM network adapter was configured as follows:
​Adapter 1: Attached to NatNetwork
​Network: NatNetwork
​Adapter Type: Intel PRO/1000 MT Desktop
​The VM was allocated:
​RAM: 2048 MB
​(Screenshot of VirtualBox settings showing Adapter 1 attached to NAT Network, Intel PRO/1000 MT Desktop, and RAM set to 2048 MB)
​A shared folder was also configured for transferring files between the host operating system and the Kali VM.
​Step 5. Configure the Kali Linux Network
​The Kali Linux virtual network was checked and configured with a consistent IPv4 address.
​Example configuration:
​IP Address: 10.0.0.2
​Subnet Mask: 255.255.255.0
​Gateway: 10.0.0.1
​DNS: 8.8.8.8
​A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.
​(Screenshot of Kali Linux network connection settings showing IPv4 address 10.0.0.2, Netmask 255.255.255.0, Gateway 10.0.0.1, and DNS 8.8.8.8)
​Step 6. Create a Clean VM Snapshot
​After completing the initial configuration, a VirtualBox snapshot was created.
​Example snapshot name: Clean Kali - Network Setup
​The snapshot represents the clean baseline of the laboratory.
​If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.
​✅ Lab Verification

Test
Command
Expected Result
Check IP Address
ip a
Correct Kali-IP displayed
Test Gateway
ping 10.0.0.1
Successful replies
Test Internet Connectivity
ping 8.8.8.8
Successful replies
Test DNS Resolution
nslookup networkwalks.com
Domain resolves
Verify Nmap
nmap -version
Nmap version displayed
Verify Snapshot
Restore snapshot and run ip a
Baseline configuration restored

Example Results:
​IP Address: 10.0.0.2
​Gateway: 10.0.0.1
​DNS: 8.8.8.8
​🛠️ Problems Encountered & Solutions
​Documenting problems is an important part of the project.
​Problem 1. Internet Connectivity After Static IP Configuration
​After manually configuring the IPv4 settings, internet connectivity may fail depending on the Kali/NetworkManager configuration.
​One workaround used during this lab was: 
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
The network connection was then restarted/reconnected and connectivity was tested again.
​Important: Network interface and connection names may differ between systems. Students should first identify their actual connection name before running the nmcli command.
​Problem 2. VirtualBox VT-x / Virtualization Error
​The VM initially failed to start because hardware virtualization was disabled in the system BIOS/FIRMWARE.
​The issue was resolved by:
​Restarting the computer
​Entering BIOS/UEFI settings
​Enabling Intel VT-x / hardware virtualization
​Saving the configuration
​Restarting the computer
​Starting the Kali VM again
​After enabling virtualization, the VM started successfully.
​💡 What I Learned
​Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.
​The most important concepts I learned include:
​NAT vs NAT Network
​A standard NAT configuration and a NAT Network serve different purposes.
​A NAT Network allows multiple VMs connected to the same NAT Network to communicate with one another while also having outbound network connectivity.
​This makes it useful for building a multi-machine cybersecurity laboratory.
ry.
​Virtual Machine Networking
​I learned how VirtualBox network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.
​Static IP Configuration
​I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.
​VM Snapshots
​I learned that a clean snapshot should be created before performing risky or experimental activities.
​This provided a known-good recovery point for future cybersecurity exercises.
.
​Documentation
​I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.
​🛡️ Security & Ethical Use
​This laboratory is intended strictly for education purposes only.
​🔗 Tools & Resources
​7-Zip: https://www.7-zip.org/download.html
​VirtualBox: https://www.virtualbox.org/wiki/Downloads
​Kali Linux: https://www.kali.org/get-kali/
​📁 Project Information
​Program Name: Cybersecurity at Networkwalks / Week: 01 / Project: Cybersecurity & Penetration Testing Lab
​Setup / Repository: GitHub

