## 🌐 Networking Overview

The homelab uses VLAN segmentation to isolate lab devices from the main home network, while still allowing internet access through our ISP Gateway. This networking section governs the entire lab topology and will be expanded as new hosts and services are added.

## 🧱 Network Layout

| Role                | IP Address     | Interface         | Notes                                 |
|---------------------|----------------|-------------------|---------------------------------------|
| ISP Gateway      | 192.168.2.1    | VLAN 1 (native)   | Primary internet gateway              |
| Managed Router      | 172.16.0.1     | VLAN 10 (tagged)  | Homelab router/firewall               |
| Raspberry Pi        | 172.16.0.10    | VLAN 10 (tagged)  | Docker host + Dashy UI                |
| Future Docker Host  | 172.16.0.20    | VLAN 10 (tagged)  | Retired mini PC for lab containers    |
| Homelab Subnet      | 172.16.0.0/24  | VLAN 10           | Isolated VLAN for all lab devices     |

## 📦 VLAN Setup (NETGEAR GS308E)

| Port | Device             | VLAN 1 | VLAN 10 | Mode     |
|------|--------------------|--------|---------|----------|
| 1    | ISP Gateway     | Untagged | Excluded | Access   |
| 2    | Router WAN         | Untagged | Excluded | Access   |
| 3    | Router LAN         | Excluded | Tagged   | Trunk    |
| 4    | Raspberry Pi       | Excluded | Tagged   | Trunk    |
| 5    | Mini PC Host       | Excluded | Tagged   | Trunk    |

---

## 🔧 Next Steps
- [ ] Set static IP on the Pi
- [ ] Set up VLAN tagging for Pi and mini PC ports
- [ ] Install Docker & Dashy on Pi
- [ ] Configure firewall/NAT from homelab to Bell Giga Hub
- [ ] Acquire and provision mini PC for Docker hosting
