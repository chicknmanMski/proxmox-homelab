# proxmox-homelab
# Proxmox Cybersecurity Home Lab

A self-hosted virtualization environment built on a dedicated mini PC running Proxmox as the bare-metal OS. This lab simulates real-world network segmentation and is used to practice offensive and defensive security techniques in an isolated, controlled environment.

---

## Hardware

- **Host Machine:** Dedicated mini PC
- **Hypervisor:** Proxmox VE (bare-metal installation)
- **Purpose:** Run multiple virtual machines simultaneously, each serving a distinct role in the lab network

---

## Lab Architecture

### Virtual Machines

| VM | OS | Role |
|---|---|---|
| pfSense | FreeBSD (pfSense) | Virtual firewall and router — separates the internal LAN from the external network |
| Ubuntu-1 | Ubuntu Linux | Internal LAN device — sits behind the pfSense firewall |
| Ubuntu-2 | Ubuntu Linux | Flexible device — repositioned between internal and external zones depending on lab scenario |

### Network Topology

```
[ External / WAN Side ]
        |
   [ pfSense VM ]   ← Virtual firewall / router
   (firewall rules, traffic filtering, routing)
        |
[ Internal LAN (Proxmox) ]
        |
  [ Ubuntu-1 ]    [ Ubuntu-2 ]
  (internal)      (repositioned per scenario)
```

Ubuntu-2 is intentionally moved to the outside of the internal LAN to simulate a device operating in an untrusted zone. This allows for controlled observation of traffic entering and exiting a protected network.

---

## Lab Scenarios & Skills Demonstrated

### Network Segmentation
- Configured pfSense as a virtual firewall to enforce boundaries between LAN and WAN zones
- Applied and tested firewall rules to control traffic between network segments

### Packet Analysis
- Captured and analyzed network traffic as data moves in and out of the internal LAN
- Observed packet behavior across trusted and untrusted zones
- Tools used: `tcpdump`, `Wireshark`

### Port Scanning & Vulnerability Assessment
- Conducted `nmap` scans against lab hosts to identify open ports
- Identified and remediated unintended open ports across the internal network
- Practiced recon techniques in a legal, isolated environment

---

## Key Concepts Practiced

- **Network segmentation** — enforcing logical boundaries between zones
- **Firewall rule creation** — writing and testing pfSense rules
- **Traffic analysis** — reading and interpreting packet captures
- **Reconnaissance** — using nmap to map a network and assess exposure
- **VM networking** — configuring virtual network interfaces in Proxmox

---

## Tools & Technologies

- Proxmox VE
- pfSense
- Ubuntu Linux
- nmap
- Wireshark / tcpdump

---

## Purpose

This lab was built to develop hands-on skills in network security, traffic analysis, and firewall administration in a safe, self-contained environment. All activity is conducted exclusively within this private lab network.

---

## Notes

This repository documents infrastructure and methodology. No sensitive configurations, credentials, or proprietary data are included.
