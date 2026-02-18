# Homelab Network Architecture

## Overview

This homelab simulates a small secure network environment including:

- Segmented lab network behind OPNsense
- Raspberry Pi 4 acting as internal server
- Network surveillance cameras
- Cloudflare tunnel for secure external access
- Backup ISP WiFi network

---

## Physical & Logical Topology

Internet
   │
Modem (ISP Router)
   │
┌───────────────┬─────────────────────────┐
│               │
Backup WiFi     WAN → OPNsense (MacBook)
(Separate SSID)         │
                        │
                   LAN Interface
                        │
                  Access Point
                        │
                Homelab WiFi
                        │
                   Raspberry Pi 4
                        │
     ┌───────────────┬───────────────┬───────────────┐
     │               │               │
  Web Server      Printer      External HDD
     │
     └───────────────┬────────────────────────┐
                     │                        │
               Network Camera 1        Network Camera 2
