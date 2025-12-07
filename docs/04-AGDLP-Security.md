# 4. AGDLP Security Model

## Philosophy
To maintain a scalable environment, permissions are never assigned to Users directly.   
We strictly follow the **AGDLP** principle:  
**A**ccounts > **G**lobal Groups > **D**omain **L**ocal Groups > **P**ermissions.

* **Global Groups (GG):** Represent *Roles* or *Departments* (Who are you?)
* **Domain Local Groups (DL):** Represent *Access Levels* on Resources (What can you do?)

## Implementation Example: Sales Printer
*Requirement: The Sales Leads must be able to manage print jobs on their own printer.*

| Stage | Object Name | Description |
| :--- | :--- | :--- |
| **Account** | `killiankelley` | The User (Head of Sales) |
| **Global Group** | `GG_Sales_Leads` | Contains all Sales Managers |
| **Domain Local** | `DL_Printer_Sales_Manage` | "Manage Documents" permission on Sales Printer |
| **Permission** | ACL on `PR-SAL-04` |  Allow "Manage Documents" |

**Description:**
* Screenshot 1 showing the Security Tab of PR-SAL-04 printer with `DL_Printer_Sales_Manage` added and given the Manage Documents permission
* Screenshot 2 showing `GG_Sales_Leads` as a member of `DL_Printer_Sales_Manage`.

![PR-SAL-04](..\images\Security-PR-SAL-04.png)  
![Memberof-GG_Sales_Leads](..\images\Memberof-GG_Sales_Leads.png)  

**Result:** Killian Kelly, Head of Sales, member of GG_Sales_Leads, can manage printjobs on `PR-SAL-04`.

## Practical example: Sales Printer
If a new Sales Manager is hired, we simply add them to `GG_Sales_Leads`. They automatically inherit permissions to files, printers, and intranet sites without us modifying any ACLs on the servers.

## Implementation Example: Department Share
*Requirement: The Sales Team must be able to modify their own department directory.*

| Stage | Object Name | Description |
| :--- | :--- | :--- |
| **Account** | `killiankelley` | The User (Head of Sales) |
| **Global Group** | `GG_Sales_Team` | Contains all Sales Leads + Staff |
| **Domain Local** | `DL_Share_Sales_Modify` | Modify permission on Sales share |
| **Permission** | ACL on `\\FS01\Sales` |  Allow "Modify" |

**Description:**
* Screenshot 1 showing the Security Tab of the shared Sales directory with `DL_Share_Sales_Modify` and `DL_Share_Sales_Read`  added and given the Modify and Read permissions respectively.
* Screenshot 2 showing `GG_Sales_Team` as a member of `DL_Share_Sales_Modify`.

![Share-Sales-Security](..\images\Share-Sales-Security.png)  
![Share-Memberof-GG_Sales_Team](..\images\Share-Memberof-GG_Sales_Team.png)  

Result: Killian Kelly, Head of Sales, member of GG_Sales_Team, can modify/read the Sales share directory. 

## Practical example: Sales share
If Sales hires a new team member, we can add them to `GG_Sales_Team`. They will inherit all associated permissions, software, access to printers that are needed to operate in their respective team.