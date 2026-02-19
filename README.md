# Homelab Network Architecture

## Overview

This homelab simulates a layered, security-focused network environment designed to demonstrate practical IT support, firewall configuration, segmentation, and secure remote access.

Core components include:

- AT&T Gateway performing NAT (Layer 1)
- OPNsense firewall performing internal NAT (Layer 2)
- Segmented LAN behind OPNsense
- Raspberry Pi 4 acting as internal web server
- Network surveillance cameras on isolated VLAN
- Cloudflare Tunnel for secure external access
- Backup ISP WiFi connection (separate SSID)

This environment is used to practice real-world troubleshooting, firewall management, subnetting, VLAN segmentation, and secure remote access configuration.

## Physical & Logical Topology

```
Internet
   ↓
AT&T Gateway (NAT #1)
   ├── Backup WiFi (ISP SSID)
   │     └── WiFi Devices (Fallback Network)
   ↓
OPNsense Firewall (NAT #2)
   ├── LAN (10.0.0.0/24)
   │     ├── Raspberry Pi 4
   │     ├── Printer
   │     └── External HDD
   │
   ├── Camera VLAN (10.0.10.0/24)
   │     ├── Camera 1
   │     └── Camera 2
   │
   └── WireGuard VPN (Remote Access Endpoint)

Raspberry Pi → Encrypted Tunnel → Cloudflare
→ Internet Users
```

## Security & Network Design Principles

This lab follows foundational networking and security practices:

- Dual-layer NAT architecture
- Network segmentation between LAN and camera/IoT devices
- OPNsense firewall managing routing and access control
- No direct public port forwarding
- Secure outbound-only remote access using Cloudflare Tunnel
- Private subnet addressing for internal services
- Logical separation of WAN, LAN, and VLAN segments

These principles mirror small business and enterprise network architecture concepts.

---

## Skills Demonstrated

### Networking

- Firewall configuration (OPNsense)
- WAN/LAN interface configuration
- VLAN segmentation concepts
- Understanding NAT boundaries
- Wireless access point configuration
- Backup ISP planning awareness

### Systems & Infrastructure

- Raspberry Pi server setup and management
- Hosting internal web services
- Managing network-attached storage
- Cross-subnet connectivity troubleshooting

### Security

- Reducing attack surface (no exposed inbound ports)
- Encrypted tunnel-based remote access
- Isolating surveillance/IoT devices
- Layered network architecture design

---

## Career Objective

This homelab supports continued development toward:

- IT Support / Helpdesk
- Junior Network Administrator
- Network Operations
- Entry-Level Security-Focused IT Roles

It reflects hands-on learning beyond theory and demonstrates practical application of networking and infrastructure concepts.