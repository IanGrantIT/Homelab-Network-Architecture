# Homelab Network Architecture

## Overview

This homelab simulates a layered, security-focused network environment designed to demonstrate practical IT support, firewall configuration, segmentation, and secure remote access.

Core components include:

- AT&T Gateway in Bridge Mode
- OPNsense firewall
- Segmented LAN behind OPNsense
- Raspberry Pi 4 acting as internal web server
- Network surveillance cameras on isolated VLAN
- Cloudflare Tunnel for secure external access

This environment is used to practice real-world troubleshooting, firewall management, subnetting, VLAN segmentation, and secure remote access configuration.

## Physical & Logical Topology

```
Internet
   ↓
Edge Network
   ↓
AT&T Gateway (Bridge mode)
   ↓
OPNsense Firewall (Wireguard VPN)
   ├── LAN → Core Network (10.0.0.0/24)
   │     └── Switch (Netgear GS305E)
   │          ├── TP-Link EAP610 → Wi-Fi
   │          ├──  Raspberry Pi 4 (Tailscale)
   │             ├── Printer (CUPS)
   │             ├──Web Server(Nginx,Cloudflare)
   │             └──Pi-hole (DNS filtering)
   │          └── Ubuntu Laptop (Mac A1466)
   │            ├── Docker (Tailscale)
   │            ├── Grafana
   │            ├── Prometheus
   │            ├── VPN container
   │            ├── Media Server (Jellyfin)
   │            └── External Hard Drive
   │
   ├── VLAN2→Security Cameras(ID: 20)(10.0.20.0/24)
   │     ├── Camera 1
   │     └── Camera 2
   │
   ├── VLAN3→VPN Network(ID: 30)(10.0.30.0/24)
   │
   │
   └── VLAN4 → Servers (ID: 40) (10.0.40.0/24)
         ├── Website
         ├── Printer
         ├── Jellyfin
         └── External Hard Drive

DNS Flow:
  All VLANs
      ↓
  OPNsense DHCP (forces Pi as DNS)
      ↓
  Raspberry Pi (Pi-hole)
      ↓
  Upstream Resolver (Unbound / Cloudflare / ISP)
  
Remote Access Flow:
  Remote Device (Laptop / Phone)
      ↓
  Encrypted Tunnel (WireGuard or Tailscale)
      ↓
  OPNsense Firewall
      ↓
  Internal VLAN Networks
      ↓
  Homelab Services (Pi-hole / Grafana / Jellyfin / Servers)
```
## Example Traffic Flow

### Example 1 — Client Browsing the Internet

User Device (Wi-Fi or LAN)  
↓  
TP-Link EAP610 Access Point  
↓  
Netgear GS305E Switch  
↓  
OPNsense Firewall  
↓  
NAT Translation  
↓  
AT&T Gateway (Bridge Mode)  
↓  
Internet

---

### Example 2 — DNS Request

Client Device  
↓  
OPNsense DHCP assigns Pi-hole as DNS server  
↓  
Raspberry Pi (Pi-hole DNS filtering)  
↓  
Upstream Resolver (Unbound / Cloudflare / ISP)  
↓  
Domain IP returned to client

---

### Example 3 — Remote VPN Access

Remote Laptop / Phone  
↓  
Encrypted Tunnel (WireGuard or Tailscale)  
↓  
OPNsense Firewall  
↓  
Internal VLAN Network  
↓  
Access to services (Grafana / Jellyfin / Pi-hole)

---

### Example 4 — Public Website Access

Internet User  
↓  
Cloudflare Network  
↓  
Cloudflare Tunnel  
↓  
Raspberry Pi Web Server (Nginx)  
↓  
Internal service response
## Key Technologies

• OPNsense Firewall  
• VLAN Segmentation  
• WireGuard VPN  
• Tailscale Mesh VPN  
• Pi-hole DNS Filtering  
• Docker Containerization  
• Prometheus + Grafana Monitoring  
• Cloudflare Tunnel

## Security & Network Design Principles

This lab follows foundational networking and security practices:

- Network segmentation between LAN, camera/IoT devices, and Servers
- OPNsense firewall managing routing and access control
- No direct public port forwarding
- Secure outbound-only remote access using Cloudflare Tunnel
- Private subnet addressing for internal services
- Logical separation of WAN, LAN, and VLAN segments

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
- Ad blocking/DNS filtering

---

## Career Objective

This homelab supports continued development toward:

- Junior Network Administrator
- Network Operations
- Data Center Technician
- Entry-Level Security-Focused IT Roles

It reflects hands-on learning beyond theory and demonstrates practical application of networking and infrastructure concepts.