# E-corp Project

## E-corp Documentation Overview

This repository contains the technical documentation for the IT infrastructure of a small fictional company named **E-corp**.

The primary purpose of this documentation is to provide a clear handbook and guidelines for future system administrators. The environment has been created with best practices in mind prioritizing security, scalability, and ease of management.

### Design Philosophies

* **Scalability & Isolation:** Identity services (DC01) are separated from File/Print services (FS01) to prevent single points of failure, minimize the Domain Controller attack surface and allow for scaling.
* **AGDLP Security Model:** The **A**ccount > **G**lobal Group > **D**omain **L**ocal Group > **P**ermission model was used. This ensures permissions are never assigned to individual users, keeping the environment clean and manageable as staff changes.
* **Automated Management:** Software deployment, drive mapping, and printer installation are fully automated via Group Policy Objects (GPO). Eliminating the need for manual configuration on every single end device.

## Test Credentials

The following accounts have been created to allow the external auditor to verify the configuration.

**Default Password for all audit accounts:** `Ecorp@udit2025`  

| Role | Username | Department |
| :--- | :--- | :--- |
| **CEO** | `auditceo` | Management |
| **Sales Staff** | `auditsalesstaff` | Sales |
| **Head of RnD** | `auditrndhead` | Research and Development |
| **RnD Staff** | `auditrndstaff` | Research and Development - Fidget Spitters |

## Table of Contents

- [0. Table of Contents](docs/00-Table-of-Contents.md)
- [1. Installation & Architecture](docs/01-Installation-Architecture.md#1-installation---architecture)
  * [Hardware specifications](docs/01-Installation-Architecture.md#hardware-specifications)
  * [Installation](docs/01-Installation-Architecture.md#installation)
  * [Storage Layout](docs/01-Installation-Architecture.md#storage-layout)
  * [Server Layout](docs/01-Installation-Architecture.md#server-layout)
  * [Networking](docs/01-Installation-Architecture.md#networking)
    + [General overview](docs/01-Installation-Architecture.md#general-overview)
    + [DC01](docs/01-Installation-Architecture.md#dc01)
    + [FS01](docs/01-Installation-Architecture.md#fs01)
    + [DHCP](docs/01-Installation-Architecture.md#dhcp)
    + [DNS](docs/01-Installation-Architecture.md#dns)
- [2. Naming Conventions](docs/02-Naming-Conventions.md#2-naming-conventions)
  * [Philosophy](docs/02-Naming-Conventions.md#philosophy)
  * [Organizational Units (OU)](docs/02-Naming-Conventions.md#organizational-units--ou-)
    + [Department Naming](docs/02-Naming-Conventions.md#department-naming)
    + [Directory Structure](docs/02-Naming-Conventions.md#directory-structure)
  * [Users](docs/02-Naming-Conventions.md#users)
  * [Groups](docs/02-Naming-Conventions.md#groups)
    + [Global Groups (GG)](docs/02-Naming-Conventions.md#global-groups--gg-)
    + [Domain Local Groups (DL)](docs/02-Naming-Conventions.md#domain-local-groups--dl-)
  * [Group Policy Objects (GPO)](docs/02-Naming-Conventions.md#group-policy-objects--gpo-)
  * [Devices](docs/02-Naming-Conventions.md#devices)
    + [Servers](docs/02-Naming-Conventions.md#servers)
    + [Computers](docs/02-Naming-Conventions.md#computers)
    + [Printers](docs/02-Naming-Conventions.md#printers)
- [3. Active Directory](docs/03-Active-Directory.md#3-active-directory)
  * [OU Structure](docs/03-Active-Directory.md#ou-structure)
- [4. AGDLP Security Model](docs/04-AGDLP-Security.md#4-agdlp-security-model)
  * [Philosophy](docs/04-AGDLP-Security.md#philosophy)
  * [Implementation Example: Sales Printer](docs/04-AGDLP-Security.md#implementation-example--sales-printer)
  * [Practical example](docs/04-AGDLP-Security.md#practical-example)
  * [Implementation Example: Department Share](docs/04-AGDLP-Security.md#implementation-example--department-share)
  * [Practical example: Sales share](docs/04-AGDLP-Security.md#practical-example--sales-share)
- [5. Storage & File Sharing](docs/05-Storage-File-Sharing.md#5-storage---file-sharing)
  * [Root Structure](docs/05-Storage-File-Sharing.md#root-structure)
  * [Security Features](docs/05-Storage-File-Sharing.md#security-features)
  * [Directory Structure](docs/05-Storage-File-Sharing.md#directory-structure)
  * [File Shares & AGDLP](docs/05-Storage-File-Sharing.md#file-shares---agdlp)
- [6. Printers](docs/06-Printers.md#6-printers)
  * [Overview](docs/06-Printers.md#overview)
  * [AGDLP Configuration](docs/06-Printers.md#agdlp-configuration)
- [7. Group Policy Configuration](docs/07-Group-Policies.md#7-group-policy-configuration)
  * [GPO Summary Table](docs/07-Group-Policies.md#gpo-summary-table)
- [08. Backup Shedules](docs/08-Backup-Shedules.md#08-backup-shedules)
  * [Windows Server Backup](docs/08-Backup-Shedules.md#windows-server-backup)
