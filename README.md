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

// Credits

Shared by [YourName](https://github.com/YourUsername)

---


 


