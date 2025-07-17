# Buffed Rocket Sentry
A Cheat Engine table using the MIAUSISI Weapons Balance Patch Base.

## Summary
![Rocket_Sentry_Stratagem_Icon](https://github.com/user-attachments/assets/6dae21ef-d322-4216-b651-0a588559a2d5)  
Image credit: https://helldivers.wiki.gg/ & Arrowhead Game Studios
* Author: **Knitby**
* WBP Version: v3.3.1+
* Description: Adjusts values for the **A/MLS-4X Rocket Sentry**, it has a much faster projectile velocity, with being able to punch through thicker armor, a wider and stronger explosive force, and higher damage across the board.
* Balancing Evaluation: Slightly unbalanced due to the damage and stagger boost, makes the sentry able to hold its own even better, but not enough for it to become a one-man-army/turret.

## Instructions
1. Start by locating the 【﻿ＴＵＲＲＥＴＳ　ＡＮＤ　ＲＥＬＡＹＳ】 script group.
   ![Turrets & Relays in Cheat Table](https://github.com/user-attachments/assets/0a06c606-17ce-40e1-b4c7-b7129e17ea66)
2. Right click on the script group and click on "Change script".
3. Within the code, create a new block of code and paste the following code within it:
   ```lua
   --//      A/MLS-4X Rocket Sentry
   rocketsentry_projectile   = Read_ProjectileInfo_Data("ProjectileType_Rocket_70mm_turret", 3965302274531977670)
   rocketsentry_prj_damage   = Read_DamageSettings_Data("DamageInfoType_Projectile_Rocket_70mm")
   rocketsentry_exp_damage   = Read_DamageSettings_Data("DamageInfoType_Explosion_Projectile_Rocket_70mm")
   rocketsentry_explosive    = Read_ExplosiveSettings_Data("ExplosionType_Rocket_70mm_turret")
   ```
   After pasting the code into the group's code, it should now look like this:
   ![Read Data Code Preview](https://github.com/user-attachments/assets/b5902f23-87d3-43da-b530-54d09d380c64)
> [!TIP]
> Press 'Enter' on your keyboard twice to create a new paragraph/block of code.

4. Copy and paste the following script on to the script group:
   ```lua
   <?xml version="1.0" encoding="utf-8"?>
   <CheatTable>
     <CheatEntries>
       <CheatEntry>
         <ID>8224</ID>
         <Description>"[TURRET] A/MLS-4X Rocket Sentry"</Description>
         <LastState Activated="1"/>
         <Color>CC9797</Color>
         <VariableType>Auto Assembler Script</VariableType>
         <AssemblerScript>
   [ENABLE]
   {
       Game       : helldivers2.exe
       Version    : 1.003.105
       Date       : 2025-14-07
       Author     : Knitby (!!HUGE CREDITS TO MIAUSISI FOR WBP!!)
   }
   {$lua}
   --//! A/MLS-4X Rocket Sentry Projectile
   rocketsentry_prj_damage.DATA.damage_std         = 950
   rocketsentry_prj_damage.DATA.damage_drb         = 950
   rocketsentry_prj_damage.DATA.ap_vals.ap1        = 6
   rocketsentry_prj_damage.DATA.ap_vals.ap2        = 6
   rocketsentry_prj_damage.DATA.ap_vals.ap3        = 5
   rocketsentry_prj_damage.DATA.ap_vals.ap4        = 5
   rocketsentry_prj_damage.DATA.momentum.stagger   = 45
   rocketsentry_prj_damage.DATA.momentum.knkback   = 30
   
   rocketsentry_projectile.DATA.speed        = 600
   rocketsentry_projectile.DATA.life_time    = 20
   
   --//! A/MLS-4X Rocket Sentry Explosion
   rocketsentry_exp_damage.DATA.damage_std     = 400
   rocketsentry_exp_damage.DATA.damage_drb     = 400
   rocketsentry_exp_damage.DATA.ap_vals.ap1    = 4
   rocketsentry_exp_damage.DATA.ap_vals.ap2    = 4
   rocketsentry_exp_damage.DATA.ap_vals.ap3    = 3
   rocketsentry_exp_damage.DATA.ap_vals.ap4    = 3
   
   rocketsentry_explosive.DATA.inner_radius    = 5.0
   rocketsentry_explosive.DATA.outer_radius    = 6.0
   rocketsentry_explosive.DATA.inner_radius    = 10.0
   
   
   Apply_DamageSettings_Modifications(rocketsentry_prj_damage.DATA)
   Apply_ProjectileInfo_Modifications(rocketsentry_projectile.DATA)
   Apply_DamageSettings_Modifications(rocketsentry_exp_damage.DATA)
   Apply_ExplosiveSettings_Modifications(rocketsentry_explosive.DATA)
   
   {$asm}
   [DISABLE]
   {$lua}
   
   Apply_DamageSettings_Modifications(rocketsentry_prj_damage.backup)
   Apply_ProjectileInfo_Modifications(rocketsentry_projectile.backup)
   Apply_DamageSettings_Modifications(rocketsentry_exp_damage.backup)
   Apply_ExplosiveSettings_Modifications(rocketsentry_explosive.backup)
         </AssemblerScript>
       </CheatEntry>
     </CheatEntries>
   </CheatTable>
   ```
     After pasting the script, you should now have something like this in your Cheat Table:
  ![Pasted Rocket Sentry Script Result](https://github.com/user-attachments/assets/0cac6482-906d-4b4f-b69e-9111dbe28127)
> [!WARNING]
> Ensure that you are not copy-pasting into the 【﻿ＴＵＲＲＥＴＳ　ＡＮＤ　ＲＥＬＡＹＳ】 script group's code, you merely have to right click on the group and press 'Paste'.

5. Click and hold to drag the new script so that it is now nested into the script group, you can place the script wherever you want, as long as it is within 【﻿ＴＵＲＲＥＴＳ　ＡＮＤ　ＲＥＬＡＹＳ】.
   ![New Script Nested Location](https://github.com/user-attachments/assets/238f76f0-7416-4551-8396-6d1560bf31b6)
6. **(OPTIONAL)** You may choose to adjust the values yourself if you feel like the sentry is too strong or too weak, just right click on the script and hit 'Change script'.
7. Activate the 【﻿ＣＯＲＥ】 and the 【﻿ＴＵＲＲＥＴＳ　ＡＮＤ　ＲＥＬＡＹＳ】 script group and then the script itself, make sure that you do this **<ins>BEFORE</ins>** calling down the sentry stratagem. Otherwise enjoy your new Rocket Sentry and have fun spreading Managed Democracy! o7
