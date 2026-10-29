# Cybersecurity-Lab-Setup
Cybersecurity Lab Setup - kali Linux and VirtualBox
<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
 <img src="https://img.shields.io/badge/SOC-0070C0?style=flat-square&logo=shieldsdotio&logoColor=white" />
</p>

---

## 📌 Project Overview

This project involves creating an isolated virtual lab for hands-on cybersecurity practice using Kali Linux and VirtualBox.

The setup provides a space to explore network discovery, information gathering, security weaknesses, and other practical security techniques without testing against real-world systems.

The virtual network is designed to support future expansion by allowing more virtual machines to be connected for controlled testing and experimentation.

---

## 🛡️ Purpose of the Lab

The lab offers a safe, isolated space to develop practical cybersecurity skills and carry out authorized security exercises.

Possible activities include:

- Discovering devices and gathering network information
- Scanning ports to identify exposed services
- Checking systems for potential vulnerabilities
- Examining network traffic with packet analysis tools
- Practicing web application security testing
- Learning how exploitation techniques work in a controlled setting
- Testing cybersecurity tools and exploring their capabilities

# N.B: For Educational purpose only

## ⚙️ Lab Configuration

| 🧩 Component       | ⚙️ Configuration   |
| ------------------ | ------------------  |
| 🖥️ Host OS         | Windows 11 pro      |
| 🧠 Host RAM        | 16 GB               |
| ⚡ Processor       | Intel Core i5      |
| 🧰 Hypervisor      | VirtualBox 7.2.14  |
| 🐉 Security OS     | Kali Linux 2026.2  |
| 🧠 Kali RAM        | 2048 MB            |
| 🌐 Virtual Network | NAT Network        |
| 📡 Network Address | 10.0.0.0/24        |
| 🐧 Kali IP Address | 10.0.0.2/24        |
| 🚪 Default Gateway | 10.0.0.1           |
| 🌍 DNS Server      | 8.8.8.8            |

---

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
```text
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled
```

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

![image alt](https://github.com/emmy325/Cybersecurity-Lab-Setup/blob/5fa69aa3724733662141fab4e5fd87498361f7c2/Screenshot%202026-10-26%20115716.png)


## Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```text
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
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

![image alt](https://github.com/emmy325/Cybersecurity-Lab-Setup/blob/c293e699e1e728425a305df6342d1e3cf7c60cfd/Screenshot%202026-10-26%20125943.png)

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.


---


# When all the steps are done, you can check the ip and ping for connectivity

---

## 🔎 Lab Verification

| ✅ Test | 🧾 Command | 🎯 Expected Result |
|---|---|---|
| 🌐 Check IP address | `ip a` | Kali's assigned IP address is displayed |
| 📡 Test gateway connectivity | `ping 10.0.0.1` | Replies received from the gateway |
| 🌍 Test Internet connectivity | `ping 8.8.8.8` | Replies received from Google's DNS IP |
| 🔎 Verify DNS resolution | `nslookup http.kali.org 8.8.8.8` | Domain resolves to an IP address |
| 🧰 Verify Nmap installation | `nmap --version` | Installed Nmap version is displayed |
| 📸 Verify snapshot | Restore the saved snapshot and run `ip a` | The virtual machine returns to its saved state |

---


## Problems Encountered and Solutions

**1. Virtualization Disabled:** Virtualization was initially disabled on my PC, preventing the virtual environment from running properly. I restarted the PC, entered the BIOS/UEFI settings, and enabled virtualization.

**2. DNS Resolution Issue:** After configuring the static IP address, I encountered difficulties resolving domain names using the local DNS server (`10.0.0.1`). Although both DNS options can work, I used Google's public DNS (`8.8.8.8`), which successfully resolved domain names in my lab.
## What I Learned

- **NAT Network:** Learned how to configure a NAT Network in VirtualBox to allow virtual machines on the same network to communicate with each other while accessing external networks.
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



