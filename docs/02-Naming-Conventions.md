# 2. Naming Conventions

## Philosophy
* **Goal:** Readable, understandable, minimize confusion, manageable syntax in scripts.
* **Format:** Full-length words. Minimize abbreviations or truncating of names (unless explicitly noted). No spaces (` `).
* **Separators:** Underscores `_` and Dashes `-` are used for separation.

## Organizational Units (OU)

### Department Naming
**Capitalisation:** `CamelCase`

| Department Name | OU Name |
| :--- | :--- |
| IT Department | `_Admin` |
| Executive Department | `Management` |
| Payroll and Human Resources | `PayrollHumanResources` |
| Research and Development | `ResearchAndDevelopment` |
| Sales Department | `Sales` |
| Supply Chain Department | `SupplyChain` |

### OU Directory Structure
```
E-Corp
├── _Admins
├── _Groups
├── Users
│   ├── Management
│   ├── PayrollHumanResources
│   ├── ResearchAndDevelopment
│   │   ├── FidgetSpitters
│   │   ├── Pokamans
│   │   └── WorldOfMycraft
│   ├── Sales
│   └── SupplyChain
└── Computers
    ├── General
    └── Sales
```

## Users

**Capitalization:** lowercase  
**Syntax:** `<firstname><lastname>@ad.ecorp.internal`

| Attribute | Value |
| :--- | :--- |
| First Name | Lillith |
| Initials | N |
| Last Name | Regan |
| **User Logon Name** | `lillithregan@ad.ecorp.internal` |

## Groups
### Global Groups (GG)
**Capitalization:** CamelCase  
**Syntax:** `GG_<MainDepartment>_<SubDepartment>_<EmployeeGroup>`

*Note: `<SubDepartment>` is optional and only used if part of a Main Department.*

**Definitions:**

| Variable | Value | Notes |
| :--- | :--- | :--- |
| **GroupType** | `GG` | Global Group |
| **Main Department** | [Department Name] | See OU list above |
| **Sub Department** | [Sub-Dept Name] | `FidgetSpitters`, `Pokamans`, `WorldOfMycraft` |
| **Employee Group** | [Role] | `Executive`, `Leads`, `Staff`, `Team` (Lead + Staff) |

**Examples:**
* `GG_Management_Executive`
* `GG_ResearchAndDevelopment_FidgetSpitters_Team`

### Domain Local Groups (DL)
**Capitalization:** CamelCase  
**Syntax:** `DL_<ItemType>_<Path_To_Resource or MainDepartment>_<Permission>`

**Definitions:**
| Variable | Value | Notes |
| :--- | :--- | :--- |
| **GroupType** | `DL` | Domain Local Groups |
| **ItemType** | `Share`, `Printer` | The type of resource this applies to |
| **Path_To_Directory or MainDepartement** | `Sales` | Path from Root to Subdirectory or Main Departement |
| **Permission** | `Modify`, `Read`, `Print` | The type of permission granted |

**Examples:**
* **Share:** `\\FS01\Management` -> `DL_Share_Management_Modify`
* **Share (Sub):** `\\FS01\ResearchAndDevelopment\Pokamans` -> `DL_Share_ResearchAndDevelopment_Pokamans_Read`
* **Printer:** `DL_Printer_Sales_Print`

## Group Policy Objects (GPO)
**Capitalization:** CamelCase  
**Syntax:**
`<Applies-to>_<Purpose/Task>_<Specific>`

**Definitions:**
* **Applies to:** Target (e.g., `Users`)
* **Purpose:** Broad category (e.g., `FolderRedirection`)
* **Specific:** Specific configuration details (e.g., `DesktopDocuments`)

**Example:**
* `Users_FolderRedirection_DesktopDocuments`
* `Computers_InstallSoftware_7zip`

## Devices
### Servers
**Capitalization:** Uppercase  
**Syntax:** `<Type><##>`

| Type | Role | Name |
| :--- | :--- | :--- |
| **DC** | Domain Controller | `DC01` |
| **FS** | File Server | `FS01` |

### Computers
**Capitalization:** Uppercase  
**Syntax:** `PC<##>`

**Example:** `PC01`, `PC02`

### Printers
**Capitalization:** Uppercase  
**Syntax:** `PR-<DEPARTMENT-CODE>-<##>`

**Department Codes:** 

| Department | Code |
| :--- | :--- |
| Management | `MAN` |
| PayrollHumanResources | `PHR` |
| ResearchAndDevelopment | `RND` |
| Sales | `SAL` |
| SupplyChain | `SUP` |

**Examples:**
* `PR-MAN-01`
* `PR-SAL-04`