# 1. Installation & Architecture

## Hardware specifications

Both servers have the same hardware components and specifications.

| Component type | Full Product name + Model number |
|---|---|
| Server Chassis | Dell PowerEdge R760 (2U Rack) |
| CPU | 2 * Intel Xeon Platinum 8570 (32-core each, 64 cores total) |
| RAM | 256GB (8 * Samsung 32GB DDR5-4800 RDIMM ECC) |
| Boot Storage | Dell 400-BSKH 960GB M.2 2280 PCIe Gen4 NVMe SSD |
| Data Storage | Samsung PM893 3.84TB SATA SSD  |
| Backup Storage | Seagate Exos X12 12TB SAS ST12000NM0017 |
| Network Adapter | Intel X710-DA4 (4 * 10GbE SFP+) |
| PSU | 2 * 1400W Dell 80+ Platinum Hot-Swap PSU |
| OS | Windows Server 2025 |

## Installation

- **OS version:** Windows Server 2025 (64-bit)
- **ISO:** 26100.1742.240906-0331.ge_release_svc_refresh_SERVER_EVAL_x64FRE_en-us.iso
- **ISO SHA256:** D0EF4502E350E3C6C53C15B1B3020D38A5DED011BF04998E950720AC8579B23D

## Storage Layout

Both servers are configured with a 3-disk structure to isolate System, Data and Backup.

| Disk # | Type | File System | Drive Letter | Label | Size | Purpose |
| ---: | :--- | :--- | :--- | :--- | ---: | :--- |
| 0 | NVME | NTFS | `C:` | System | 960GB | Windows System Files |
| 1 | SSD | NTFS | `D:` | Data | 3.84TB | AD Database, SYSVOL, User Data, Shares |
| 2 | HDD | NTFS | `E:` | Backup | 12TB | Backup destination |

## Server Layout

| Server | Roles | Purpose |
| :--- | :--- | :--- |
| DC01 | Active Directory, DNS, DHCP | Handle identity, resolution and addressing |
| FS01 | File Server, Print Server | Handle file shares and printing |

## Networking

### General overview
* **Domain Name:** `ad.ecorp.internal`
* **NetBIOS:** `ECORP`
* **Network:** `10.0.0.0/24`
* **Router / Default Gateway:** `10.0.0.1`
* **Fixed IP Range:** `10.0.0.2` - `10.0.0.99`
    - **Servers:** `10.0.0.2` - `10.0.0.19`
    - **Printers:** `10.0.0.20` - `10.0.0.29`
    - **Telephony:** `10.0.0.30` - `10.0.0.79`
* **DHCP IP Range:** `10.0.0.100` - `10.0.0.254`

###  DC01 
* **Hostname:** `DC01`
* **FQDN:**	`DC01.ad.ecorp.internal`
* **IP:** `10.0.0.2`
* **Subnet Mask:** `255.255.255.0`
* **Default Gateway:** `10.0.0.1`
* **DNS:** `127.0.0.1`

###  FS01
* **Hostname:** `FS01`
* **FQDN:**	`FS01.ad.ecorp.internal`
* **IP:** `10.0.0.3`
* **Subnet Mask:** `255.255.255.0`
* **Default Gateway:** `10.0.0.1`
* **DNS:** `10.0.0.2`

### DHCP
* **DHCP Scope Name:** DHCP_Clients
* **Start IP:** `10.0.0.100`
* **End IP:** `10.0.0.254`
* **Subnet Mask** `255.255.255.0`
* **Lease Time:** `8 days`
* **Default Gateway:** `10.0.0.1` 

### DNS
* **Primary DNS Suffix:** `ad.ecorp.internal`
* **DNS IP:** `10.0.0.2`
