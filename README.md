# PiBox Setup Guide

This guide describes the setup process for my PiBox (a Raspberry Pi with a SATA hat). It includes all the software configurations required to replicate the setup without searching for details again.

**Installation will some time be obsolete, so please refer to the official documentation for the most up-to-date information.**

## Main Goals

- A case for a 3.5" HDD.
- Raspberry Pi setup.
- SSD boot from USB.
- Docker for service management.
  - All possible services running in Docker containers.

## Services

- **Samba**: File sharing.
- **Rsync**: Data synchronization and backup.
- **Grafana**: Monitor Raspberry Pi statistics (CPU, RAM, Disk, Network).
- **Pi-hole**: Local DNS for ad blocking.
- **Home Assistant**: Smart home automation.
- **WireGuard VPN**: Secure remote access.
- **NGINX with Let's Encrypt**: Web server with SSL certificates.
- **Cockpit**: Server monitoring.