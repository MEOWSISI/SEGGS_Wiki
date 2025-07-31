# SEGGS HOW-TO
## Weapon Magazine Editing
*Author: Prodihue*

This is a guide on how to change weapon magazine values including magazine size, total magazine capacity, starting magazine, and magazines refilled. 

## Category
1. [Magazine.DATA](#1-magazinedata)  
2. [Rounds.DATA](#2-roundsdata)  
3. [Entity Delta](#3-entity-delta)
4. [Comment](#4-comment)
	
I've classified weapons into three categories depending on the logic. 
This guide assumes you're responsibly enclosing all scripts within,
> [ENABLE]  
{$lua}  
--  
{$asm}

And,
>[DISABLE]  
{$lua}

### 1. 	Magazine.DATA  
* By default, this is what you should try first. I will use Tenderizer as an example of this category.  
    1. `【 ＡＵＴＯＭＡＴＩＣ ＷＥＡＰＯＮＳ 】` << This is the parent group  
        `[𝐑𝐈𝐅𝐋𝐄𝐒] 𝐀𝐑-𝟔𝟏 𝐓𝐞𝐧𝐝𝐞𝐫𝐢𝐳𝐞𝐫`   << This is the script  
        
        When adding or editing magazine capacity, both categories must be edited.  
    
    2. 	**Read Data**:  
        Within the parent group, the following must be added in this format:
       	
            (weapon_name)_magazine  =  Read_Magazine_Data (UID - unique for every weapon)  
       	So, for Tenderizer:
       	
            tenderizer_magazine   = Read_Magazine_Data(14845617694460717074)  
        
    4.	**Specific values**:  
        Then, within the script [𝐑𝐈𝐅𝐋𝐄𝐒] 𝐀𝐑-𝟔𝟏 𝐓𝐞𝐧𝐝𝐞𝐫𝐢𝐳𝐞𝐫, the following must be added in such format:
      	
            (weapon_name)_magazine.DATA.magazine_size = ### < size of mag  
            (weapon_name)_magazine.DATA.magazines     = ### < number of mags you drop down with  
            (weapon_name)_magazine.DATA.magazines_refill = ### < number of mags you gain when looting; number=mags added with re-supply (stratagem or backpack), number/2 rounded down=mags added with field loot (stuff on the ground)  
            (weapon_name)_magazine.DATA.magazines_max    = ### < maximum number of mags  

        So, for Tenderizer:
      	
            tenderizer_magazine.DATA.magazine_size = 35  
            tenderizer_magazine.DATA.magazines     = 5  
            tenderizer_magazine.DATA.magazines_refill = 7  
            tenderizer_magazine.DATA.magazines_max    = 7  
    
    3. 	**Applying settings**:  
        The following applies the values you designated:

            Apply_MagazineSettings_Modifications((weapon_name)_magazine.DATA)
        
        So, for Tenderizer:
       	
            Apply_MagazineSettings_Modifications(tenderizer_magazine.DATA)
        
        The following returns the state of your magazine to default state:
       	
            [DISABLE]
            {$lua}
            Apply_MagazineSettings_Modifications((weapon_name)_magazine.backup)
        
        So, for Tenderizer:
       	
            [DISABLE]
            {$lua}
            Apply_MagazineSettings_Modifications(tenderizer_magazine.backup)
		

### 2. 	Rounds.DATA
* Any weapon that uses rounds instead of magazines falls under this category. Good examples are round-reload shotguns such as Slugger or Cookout. I will use Slugger as an example. 
	
    1. **Read Data**:  
        Within the parent group 【 ＳＨＯＴＧＵＮＳ 】, add the following:

            (weapon_name)_rounds    = Read_Rounds_Data(UID - unique for each weapon)  
 
        So, for Slugger:  
  
            slugger_rounds     		= Read_Rounds_Data(5725374950499373869)  


    2. **Specific values**:  
        Then, within the script [𝐏𝐔𝐌𝐏] 𝐒𝐆-𝟖𝐒 𝐒𝐥𝐮𝐠𝐠𝐞𝐫, the following must be added in such format:  

            (weapon_name)_rounds.DATA.mag_size.x 	= ### < size of mag (check comment)*** 
            (weapon_name)_rounds.DATA.ammo.total 	= ### < maximum amount of ammo 
            (weapon_name)_rounds.DATA.magazines_refill = ### < number of rounds you gain when looting; number=rounds added with re-supply (stratagem or backpack), number/2 rounded down=rounds added with field loot (stuff on the ground)
            (weapon_name)_rounds.DATA.ammo.init     = ### < number of rounds you drop down with 

        So, for Slugger:  

            slugger_rounds.DATA.mag_size.x = 0
            slugger_rounds.DATA.ammo.total = 60
            slugger_rounds.DATA.ammo.refill = 60
            slugger_rounds.DATA.ammo.init = 32
            
        **SPECIAL FOR ROUNDS:
        You can designate how many rounds you reload at once:  
  
            slugger_rounds.DATA.reload_amount = 2
    
        ***It seems the size of mag designated will be applied by:  
  
            (number you chose) + 8
        So, for example,
  
            slugger_rounds.DATA.mag_size.x = 100  
        will result in mag size of 108. 


    3. **Applying settings**:  
        This is essentially the same as `Magazine.DATA`.  
    
        The following applies the values you designated:  

            Apply_RoundsSettings_Modifications((weapon_name)_rounds.DATA)
    
        So, for Slugger:
            
            Apply_RoundsSettings_Modifications(slugger_rounds.DATA)
    
        The following returns the state of your magazine to default state:  

            [DISABLE]
            {$lua}
            Apply_RoundsSettings_Modifications((weapon_name)_rounds.backup)
    
        So, for Slugger: 

            [DISABLE]
            {$lua}
            Apply_RoundsSettings_Modifications(slugger_rounds.backup)
			
	
### 3. Entity Delta
* If you've made it this far, the magazine you're trying to mod is a special one that is affected by a category of modifier called EntityDeltas. 

    1. The magazine that belongs in the EntityDelta category can be found under >  𝐖𝐄𝐀𝐏𝐎𝐍 𝐌𝐀𝐆𝐀𝐙𝐈𝐍𝐄𝐒 < section.  

    2. Every magazine script is pre-made and you only need to edit the specific values to your taste.  

### 4. Comment  
  Most UID's can be found within the SEGGS table, SEGGS Wiki, or by searching the Discord channel.  
  If you have any questions, visit https://discord.com/channels/1216744023478374410/1280720330154836031 for any help!
  
  
 <sub> Thank you: DoceDeLeite, xert, and of course Miausisi </sub>
