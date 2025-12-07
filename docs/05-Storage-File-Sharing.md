# 5. Storage & File Sharing

All data is hosted on `FS01` on the `D:` drive.

## Root Structure
This table shows the root of the shares, invisible to the user. The data location is split by purpose and group.

| Folder Path | Description |
| :--- | :--- |
| `D:\DeploySoftware` | Repository for software to be deployed using MSI installers |
| `D:\EcorpData` | Root for Department shares |
| `D:\UserData` | Storage for Redirected Folders (Desktop/Documents) |

## Security Features
*  **Access Based Enumeration (ABE):** Enabled on all shares. Users cannot see folders they do not have permission to open.
*  **Hidden Shares:** Profile data is shared as `UserData$`, preventing users from browsing the user list via the network.
*  **Strict Privacy:** `UserData` permissions are set so only `CREATOR OWNER` and `SYSTEM` have full access. Management does not have read access to personal user profiles.

## Directory Structure

* **Directory convention:**
    * **Deployable Software:** Each software package has their own directory.
    * **Departments:** Each department has their own directory.
    * **Redirected Folders:** Each user has their own directory.

A tree view of the `D:` data drive.

```
├───DeploySoftware
│   ├───7zip
│   └───Chrome
├───EcorpData
│   ├───Management
│   ├───PayrollHumanResources
│   ├───ResearchAndDevelopment
│   │   ├───FidgetSpitters
│   │   ├───Pokamans
│   │   └───WorldOfMycraft
│   ├───Sales
│   └───SupplyChain
└───UserData
    ├───benbearing
    └───killiankelley
    ...
```

## File Shares & AGDLP
This table demonstrates how permissions are constructed according to the AGDLP model for the Shared Folders on `FS01`.

| Share location | Access Level | Global Groups (GG)<br>*(contains users)* | Domain Local Group<br>*(applied to ACL)* |
| :--- | :--- | :--- | :--- |
| \\\FS01\Management | Modify | `GG_Management_Executive` | `DL_Share_Management_Modify` |
| \\\FS01\Management | Read | `GG_Management_Executive` | `DL_Share_Management_Read` |
| \\\FS01\PayrollHumanResources | Modify | `GG_PayrollHumanResources_Team` | `DL_Share_PayrollHumanResources_Modify` |
| \\\FS01\PayrollHumanResources | Read | `GG_Management_Executive` | `DL_Share_PayrollHumanResources_Read` |
| \\\FS01\ResearchAndDevelopment | Modify | `GG_ResearchAndDevelopment_Leads` | `DL_Share_ResearchAndDevelopment_Modify` |
| \\\FS01\ResearchAndDevelopment | Read | `GG_ResearchAndDevelopment_Team`, `GG_Management_Executive` | `DL_Share_ResearchAndDevelopment_Read` |
| \\\FS01\ResearchAndDevelopment\FidgetSpitters | Modify | `GG_ResearchAndDevelopment_FidgetSpitters_Team` | `DL_Share_ResearchAndDevelopment_Fidget_Modify` |
| \\\FS01\ResearchAndDevelopment\Pokamans | Modify | `GG_ResearchAndDevelopment_Pokamans_Team` | `DL_Share_ResearchAndDevelopment_Pokamans_Modify` |
| \\\FS01\ResearchAndDevelopment\WorldOfMycraft | Modify | `GG_ResearchAndDevelopment_WorldOfMycraft_Team` | `DL_Share_ResearchAndDevelopment_WorldOfMycraft_Modify` |
| \\\FS01\Sales | Modify | `GG_Sales_Team` | `DL_Share_Sales_Modify` |
| \\\FS01\Sales | Read | `GG_Management_Executive` | `DL_Share_Sales_Read` |
| \\\FS01\SupplyChain | Modify | `GG_SupplyChain_Team` | `DL_Share_SupplyChain_Modify` |
| \\\FS01\SupplyChain | Read | `GG_Management_Executive` | `DL_Share_SupplyChain_Read` |