# Buffed Rocket Sentry
A Cheat Engine table using the MIAUSISI Weapons Balance Patch Base.

## Summary
![Rocket_Sentry_Stratagem_Icon](https://github.com/user-attachments/assets/6dae21ef-d322-4216-b651-0a588559a2d5)  
Image credit: https://helldivers.wiki.gg/
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
> [!TIP]
> Press 'Enter' on your keyboard twice to create a new paragraph/block of code. It should look something like this:

   ![Read Data Code Preview](https://github.com/user-attachments/assets/b5902f23-87d3-43da-b530-54d09d380c64)
