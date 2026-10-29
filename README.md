# Cybersecurity-Lab-Setup
Cybersecurity Lab Setup
<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Waqas%20Karim%20CCIE-C00000?style=flat-square" />
</p>

---

## 📌 Project Overview

This project focuses on setting up a **virtual cybersecurity and penetration-testing lab** using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

---

## 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation and so much more

# N.B: For Educational purpose only

# 🪜 Lab Setup Procedure

## Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip
![image alt](https://github.com/emmy325/Cybersecurity-Lab-Setup/blob/a833556ca1a31576579b369e5f27d74f7e7dabac/Screenshot%202026-10-26%20114226.png)

---

## Step 2. Install VirtualBox

VirtualBox was installed as the hypervisor.
![image alt](https://github.com/emmy325/Cybersecurity-Lab-Setup/blob/2b616d0c189334a199a6d60259077eee777de346/Screenshot%202026-10-26%20114421.png)

---

## Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration:
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled
![image alt](https://github.com/emmy325/Cybersecurity-Lab-Setup/blob/0f561553e3ba9734d63042de124dfd028c8eccef/Screenshot%202026-10-26%20115119.png)

---

A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

---

## Step 4. Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

```text
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
Promiscuous Mode: Allow All
```

The VM was allocated:

```text
RAM: 2048 MB
```

---


## Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```text
IP Address: 10.0.0.2
Net Mask: 24
Gateway: 10.0.0.1
DNS: 8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

![image alt](https://github.com/emmy325/Cybersecurity-Lab-Setup/blob/cdb4359af70c21ddc13876a8bc237d9aeadcc50f/Manual_Network_Config.png)

---

## Step 6. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

```text
My Fresh Kali-Linux
```

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.


---


# When all the steps are done, you can check the ip and ping for connectivity

---


## Problems Encountered and Solutions

**1. Virtualization Disabled:** Virtualization was initially disabled on my PC, preventing the virtual environment from running properly. I restarted the PC, entered the BIOS/UEFI settings, and enabled virtualization.

**2. DNS Resolution Issue:** After configuring the static IP address, the local DNS server (`10.0.0.1`) did not resolve domain names as expected. I tested connectivity and used Google's public DNS (`8.8.8.8`) to resolve the issue.

## What I Learned

- **NAT vs. NAT Network:** Learned the difference between NAT and NAT Network and how they provide external connectivity and communication between virtual machines.
- **Virtual Machine Networking:** Understood how VirtualBox network adapters affect connectivity between virtual machines.
- **Static IP Configuration:** Practiced configuring IP addresses, subnet masks, gateways, and DNS servers.
- **Snapshots:** Learned the importance of creating clean snapshots before making risky or experimental changes.
- **Technical Documentation:** Gained practical experience documenting a cybersecurity lab project using GitHub and Markdown.

---

# 🔗 Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)

---



