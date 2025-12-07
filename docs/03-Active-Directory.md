# 3. Active Directory

## OU Structure
We utilize a split OU Design separating *Users* and *Computers*. This allows for easier management. Alongside _Admins and _Groups exists to separate managing AGDLP and GPOs from Users and Computers.

**Structure:**
* Root > Type > Departement

**Hierarchy:**
* **E-corp** (Root)
    * **_Admins** (IT Accounts)
    * **_Groups** (Security Groups)
    * **Computers**
        * `Sales` 
        * `General`
    * **Users**
        * `Management`
        * `PayrollHumanResources`
        * `Sales`
        * `SupplyChain`
        * `ResearchAndDevelopment`
            * `FidgetSpitters`
            * `Pokamans`
            * `WorldOfMycraft`