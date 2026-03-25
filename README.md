# CPR#40877: Amazon ET56-Rework Software Testing Engineering Steps

This document outlines the engineering testing steps for the Amazon ET56 device rework.

---

### 1. Configuration Files

Two `.ini` files must be pushed to the secure persist partition at `/mnt/vendor/persist/` on a device running a `UserDebug` recovery package.

*   **`deviceWwanwlan.ini`**: Toggles the WWAN (Wireless Wide Area Network) feature ON.
*   **`Custom.ini`**: Manages BSP (Board Support Package) upgrade/downgrade protection and locking.

---

### 2. Procedure

A device flashed with the custom `userdebug` image will initially have the **WWAN Mobile Network** features enabled. Pushing the `deviceWwanwlan.ini` file will then disable the WWAN features.

Use the following commands to push the configuration file and reboot the device:

```bash
** adb root
** adb push deviceWwanwlan.ini /mnt/vendor/persist/
** adb reboot
``` 

### 3. Check the rebooted device UI for quick sanity as below

  *  Settings > Network and Internet > Mobile Network
  *  Settings > Network and Internet > Mobile Plan
  *  Settings > About Phone > SIM Status(SLOT 1/2)/Availability with Sim 
  *  Settings > Connected Devices > Pair new device > Available devices > Pair to visible devices
  *  Settings > Network and Internet > WiFi > Connect to Active WiFi > Check Data function on device Browser  
  *  Settings > About Phone > Model and Hardware > Model(ET56)
