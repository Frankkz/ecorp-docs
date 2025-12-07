# 7. Group Policy Configuration

We utilize a clean GPO structure, avoiding modification of the Default Domain Policy where possible.

## GPO Summary Table

| GPO Name | Linked To | Configuration Scope | Description |
| :--- | :--- | :--- | :--- |
| **Domain_PasswordPolicy_MinPasswordLength10** | `ad.ecorp.internal` | Computer | Enforces a minimum password length of 10 characters |
| **Computers_InstallSoftware_7Zip** | `ad.ecorp.internal/E-corp/Computers` | Computer | Installs 7-Zip on all computers |
| **Computers_InstallSoftware_GoogleChrome** | `ad.ecorp.internal/E-corp/Computers/Sales` | Computer | Installs Google Chrome on Sales PCs only |
| **Users_FolderRedirection_DesktopDocuments** | `ad.ecorp.internal/E-corp/Users` | User | Redirects `Desktop` and `Documents` to `\\FS01\UserData$` |
| **Users_DriveMapping_S** | `ad.ecorp.internal/E-corp/Users` | User | Maps `S:` Drive to the correct Department Share |
| **Users_DeployPrinters** | `ad.ecorp.internal/E-corp/Users` | User | Maps Department Printers using Item-Level Targeting |