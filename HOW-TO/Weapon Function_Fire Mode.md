# SEGGS HOW-TO
## Weapon Function - Fire Mode 
*Original Author: xert*

This is a guide on how to add and change weapon function - fire mode.

### 1. Designate firemode as the weapon's function.
    WEAPON_weaponinfo.DATA.rounds.left_fn = 0-7  
    WEAPON_weaponinfo.DATA.rounds.right_fn = 0-7  
`rounds.left_fn` determines what function will be available on the left side of weapon function  
`rounds.right_fn` determines what function will be available on the right side of weapon function  

  List of Weapon Function Modes:  

    * 0 = Nothing/Disable  
    * 1 = Zoom Options  
    * 2 = RPM Modes  
    * 3 = Firemode Options  
    * 4 = Swap Magazine/Ammo Type  
    * 5 = Underbarrel Flashlight  
    * 6 = Commando Guided On/Off  
    * 7 = Muzzle Velocity Options  
It should look like this:  
`WEAPON_weaponinfo.DATA.rounds.left_fn = 3`  
OR  
`WEAPON_weaponinfo.DATA.rounds.right_fn = 3`  
Only one of these needs to be used.  

### 2. Designate a fire mode for the weapon.  
Next, you need to determine which fire modes will be available for the weapon. 

    WEAPON_weaponinfo.DATA.rounds.primary_firemode = 0-7  
    WEAPON_weaponinfo.DATA.rounds.secondary_firemode = 0-7  
    WEAPON_weaponinfo.DATA.rounds.tertiary_firemode = 0-7  

List of Weapon Firing Modes:  

    * 0 = Nothing/Disable  
    * 1 = Full Auto  
    * 2 = Semi  
    * 3 = Burst  
    * 4 = All Barrel: used in "Variable" Volley/"Bushwhacker"  
    * 5 = Railgun Safe  
    * 6 = Railgun Unsafe  
    * 7 = Total: used in "Variable"  
For example, 

    WEAPON_weaponinfo.DATA.rounds.primary_firemode = 1  
    WEAPON_weaponinfo.DATA.rounds.secondary_firemode = 2  
    WEAPON_weaponinfo.DATA.rounds.tertiary_firemode = 3  
Will give you three firing options: `burst` `semi` `full auto`  

Now you know how to add and change firing mode for weapons! 




