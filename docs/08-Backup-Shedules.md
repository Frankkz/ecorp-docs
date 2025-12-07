# 08. Backup Shedules

## Windows Server Backup
Below are the backup details applied to all Windows Servers `DC01`and `FS01`.

A dedicated hard disk was selected as the backup destination with a capacity around 2 times the combined size of the System and Data drives.

* **Backup Items:** 
    * System Reserved 
    * Recovery Partition 
    * Bare Metal Recovery (BMR)
    * System State
    * System `C:`
    * Data `D:`
* **Schedule:** Daily
* **Time:** 12:00 AM
* **Backup Destination:** Disk 2, Seagate Exos X12, Size: 12TB (Previously mounted as `E:`)
