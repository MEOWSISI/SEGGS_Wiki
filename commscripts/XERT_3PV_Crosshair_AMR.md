# 3rd Person Crosshair for AMR

![ezgif-87077cc6042fd5](https://github.com/user-attachments/assets/8c94e1a4-26e2-45fd-a495-013ec437f2df)
## Summary

* Author: **xert**
* WBP Version: 3.3.2+
* Description: Allows for 3rd person view while using the AMR.

## Instructions
1. Locate the `AWP: Anti-Materiel Rifle` on [SNIPERS AND PISTOLS]
2. Disable the script.
3. Right click on the script, then Edit this script.
4. Add these lines before applying weaponinfo function:
```lua
awp_weaponinfo.DATA.scope.crosshair_uid  = 4063643672045351739
awp_weaponinfo.DATA.scope.crosshair_type = "CrosshairWeaponType_AssaultRifle"
```
5. Save, activate, then call out an AMR.
