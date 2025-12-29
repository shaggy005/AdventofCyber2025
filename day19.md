# ICS/Modbus - Claus for Concern
```
root@ip-10-48-184-165:~# nano reconnaissance.py
root@ip-10-48-184-165:~# python3 reconnaissance.py
============================================================
TBFC Drone System - Reconnaissance Report
============================================================

HOLDING REGISTERS:
------------------------------------------------------------
HR0 (Package Type): 1
  0=Christmas, 1=Eggs, 2=Baskets

HR1 (Delivery Zone): 5
  1-9=Normal zones, 10=Ocean dump

HR4 (System Signature): 666
  WARNING: Eggsploit signature detected

COILS (Boolean Flags):
------------------------------------------------------------
C10 (Inventory Verification): False
  Should be True

C11 (Protection/Override): True
  ACTIVE - System monitoring for changes

C12 (Emergency Dump): False

C13 (Audit Logging): False
  Should be True

C14 (Christmas Restored): False
  Auto-set when system is fixed

C15 (Self-Destruct Armed): False

============================================================
THREAT ASSESSMENT:
============================================================
Eggsploit framework detected
Protection mechanism active - trap is set
Package type forced to eggs
Inventory verification disabled
Audit logging disabled

REMEDIATION REQUIRED
============================================================
root@ip-10-48-184-165:~# nano restore_christmas.py
root@ip-10-48-184-165:~# python3 restore_christmas.py
============================================================
TBFC Drone System - Christmas Restoration
============================================================

Step 1: Verifying current system state...
  Package Type: 1 (1 = Eggs)
  Protection Active: True
  Self-Destruct Armed: False

Step 2: Disabling protection mechanism...
  Protection DISABLED
  Safe to proceed with changes

Step 3: Setting package type to Christmas presents...
  Package type changed to: Christmas Presents

Step 4: Enabling inventory verification...
  Inventory verification ENABLED

Step 5: Enabling audit logging...
  Audit logging ENABLED
  Future changes will be logged

Step 6: Verifying system restoration...
  Package Type: 0 (0 = Christmas)
  Christmas Restored: True
  Emergency Dump: False
  Self-Destruct Armed: False

============================================================
SUCCESS - CHRISTMAS IS SAVED
============================================================

Christmas deliveries have been restored
The drones will now deliver presents, not eggs
Check the CCTV feed to see the results

Flag: THM{eGgMas0V3r}

============================================================

Disconnected from PLC
root@ip-10-48-184-165:~# 
```
![PHOTO-2025-12-30-03-18-30](https://github.com/user-attachments/assets/e51de041-c996-4019-8f1a-cd29a6f0f988)

## What's the flag?

```
THM{eGgMas0V3r}
```
