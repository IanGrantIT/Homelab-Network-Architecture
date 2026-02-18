# Homelab Network Architecture

## Overview

This homelab simulates a small secure network environment designed to demonstrate practical IT support, network configuration, and security fundamentals.

Core components include:

- Segmented lab network behind OPNsense firewall
- Raspberry Pi 4 acting as internal server
- Network surveillance cameras on isolated segment
- Cloudflare Tunnel for secure external access
- Backup ISP WiFi connection (separate SSID)

This environment is used to practice real-world troubleshooting, firewall management, network segmentation, and secure remote access configuration.

---

## Physical & Logical Topology

```
Internet → ISP Modem
            ↓
      OPNsense (MacBook)
            ↓
        ├── LAN (Homelab WiFi)
        │     ├── Raspberry Pi 4 (Web Server)
        │     ├── Printer
        │     └── External HDD
        │
        └── Camera VLAN
              ├── Network Camera 1
              └── Network Camera 2
```
---

## Security & Network Design Principles

This lab follows several foundational security and networking practices:

- Network segmentation between LAN devices and camera/IoT devices
- OPNsense firewall managing routing and access control
- No direct public port forwarding
- Secure outbound-only remote access using Cloudflare Tunnel
- Separate SSID for backup ISP connection
- Private subnet addressing for internal services
- Logical separation of WAN, LAN, and device segments

These principles mirror real-world small business and enterprise network architecture concepts.

---

## Skills Demonstrated

This homelab demonstrates hands-on experience with:

### Networking
- Firewall configuration (OPNsense)
- WAN/LAN interface configuration
- Basic network segmentation concepts
- Wireless access point configuration
- ISP failover awareness and backup connectivity planning

### Systems & Infrastructure
- Raspberry Pi server setup and management
- Hosting internal web services
- Managing network-attached storage (External HDD)
- Device connectivity troubleshooting

### Security
- Reducing attack surface (no exposed ports)
- Encrypted tunnel-based remote access
- Isolating surveillance/IoT devices
- Understanding layered network architecture

---

## Troubleshooting & Practical Use Cases

This lab environment supports practicing:

- Diagnosing connectivity issues between LAN devices
- Firewall rule testing and adjustment
- Device isolation testing
- Internal service availability checks
- Remote access validation through secure tunnel

---

## Career Objective

This homelab is part of my ongoing development toward roles in:

- IT Support / Helpdesk
- Junior Network Administrator
- Network Operations
- Entry-Level Security-Focused IT Roles

It reflects hands-on learning beyond theory and demonstrates practical application of networking and infrastructure concepts.