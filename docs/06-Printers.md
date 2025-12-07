### 6. Printers 

## Overview
This table lists all configured printers by name and IP.
| Printer name | IP |
| --- | --- |
| PR-MAN-01 | 10.0.0.20 |
| PR-PHR-02 | 10.0.0.21 |
| PR-RND-03 | 10.0.0.22 |
| PR-SAL-04 | 10.0.0.23 |
| PR-SUP-05 | 10.0.0.24 |

## AGDLP Configuration
This table demonstrates how permissions are constructed according to the AGDLP model for the Print Server. 
| Printer Name | Access Level | Global Groups (GG) <br> *(Nested Members)* | Domain Local Group (DL) <br> *(Applied to Security Tab)* |
| :--- | :--- | :--- | :--- |
| **PR-MAN-01** | Print | `GG_Management_Executive` | `DL_Printer_Management_Print` |
| **PR-MAN-01** | Manage Documents | `GG_Management_Executive` | `DL_Printer_Management_Manage` |
| **PR-PHR-02** | Print | `GG_PayrollHumanResources_Team`, `GG_Management_Executive` | `DL_Printer_PayrollHumanResources_Print` |
| **PR-RND-03** | Print | `GG_ResearchAndDevelopment_Team`, `GG_Management_Executive` | `DL_Printer_ResearchAndDevelopment_Print` |
| **PR-RND-03** | Manage Documents | `GG_ResearchAndDevelopment_Leads` | `DL_Printer_ResearchAndDevelopment_Manage` |
| **PR-SAL-04** | Print | `GG_Sales_Team`, `GG_Management_Executive` | `DL_Printer_Sales_Print` |
| **PR-SAL-04** | Manage Documents | `GG_Sales_Leads` | `DL_Printer_Sales_Manage` |
| **PR-SUP-05** | Print | `GG_SupplyChain_Team`, `GG_Management_Executive` | `DL_Printer_SupplyChain_Print` |
| **PR-SUP-05** | Manage Documents | `GG_SupplyChain_Leads` | `DL_Printer_SupplyChain_Manage` |