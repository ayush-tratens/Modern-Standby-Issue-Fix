# Modern-Standby-Issue-Fix
Solution for random screen blackout and sleep bug caused by Modern Standby (S0 Low Power Idle) on HP Victus laptops.
# Fix: HP Victus Random Black Screen & Lock Bug (S0 Low Power Idle)

This repository documents a verified fix for an issue with HP Victus laptops where the screen randomly goes black and locks itself. This is caused by Modern Standby (S0 Low Power Idle) on Windows 11.

// Device

- HP Victus 16 (Ryzen 7 7840HS, RTX 3050, Windows 11)
- Windows Build: 26100
- 16GB RAM
- RTX 3050 6GB VRAM

// Symptoms

- Screen goes black randomly during idle or while gaming
- System appears to sleep silently (S0)
- Requires pressing power button to resume
- Game (e.g., CS2, Genshin, RDR2) closes without warning
- Event Viewer logs: `Kernel-Power 507`, `Win32k 701`

// Diagnosed Cause
Using `powercfg /a` showed:
Standby (S0 Low Power Idle) - Available

thus :
Modern Standby (S0) was active and causing stealthy sleep-like behavior.

//Fix: Disable S0 via Registry

1. Open Registry Editor:
   - `Win + R` → `regedit`
2. Go to: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power
3.  Add new `DWORD (32-bit)` named: PlatformAoAcOverride    <-- copy and paste exactly as written
Set value to: `0`
4. Reboot your system
5. Run: powercfg /a
6. → S0 should no longer be listed.

//Result

- No more random blackouts
- System behaves as expected with power settings
- Issue resolved permanently

// or use Reg File Directly
How to Use the `.reg` File to Disable Modern Standby (S0)

This `.reg` file will automatically apply the necessary registry tweak to **disable Modern Standby (S0 Low Power Idle) a feature that may cause random black screens, sleep, or lock issues on laptops like the HP Victus.

Steps to Apply:

1. Download the file:
   `Disable_Modern_Standby.reg`

2. Right-click the file → Select "Run as administrator"

3. If prompted by User Account Control (UAC), click Yes

4. You’ll see a message:
   “Are you sure you want to continue?” → Click Yes

5. Then:
   “The keys and values have been successfully added.” → Click OK
6. Reboot your laptop

7. After reboot, open Command Prompt and type:

   powercfg /a
   If you no longer see
   Standby (S0 Low Power Idle)
   the tweak worked!

//To Undo the Change:

If you want to re-enable Modern Standby, you can:

* Delete the registry key manually from:

  
  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PlatformAoAcOverride
  

// Note:

* This tweak is safe and reversible
* It forces Windows to use traditional sleep states (S3), which are more stable on gaming laptops
* It doesn't affect system performance or battery usage in a harmful way




// Credits //

Shared by ayush-tratens(https://github.com/ayush-tratens)






 


