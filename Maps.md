###Creating a Map

To create a world it is recommended that you setup a bukkit server with [worldedit ![](./images/External-Link.png)](http://dev.bukkit.org/server-mods/worldedit/) & [voxel sniper ![](./images/External-Link.png)](http://dev.bukkit.org/server-mods/voxelsniper/).
It is also recommended that worlds are created in a empty flatworld. There are several ways to do this:

__Option 1:__  
Download this level data file: [level.dat](./resources/level.dat)  
Create a empty world folder and place it in there. Then load the world.
This level.dat uses the flatworld generator with this preset string: `2;0;1;4` You can also use this string directly in minecraft for the flatworld generator settings.

__Option 2:__  
Install one of the bukkit void world generator plugins such as:  
[Bukkit - VoidGenerator ![](./images/External-Link.png)](http://dev.bukkit.org/server-mods/voidgenerator/)

`Note:` Starting to build in a void world can be a-bit tricky if you don't have world edit or voxelsniper installed since theres nothing to build on. This can be remedied by using [MCEdit ![](./images/External-Link.png)](http://www.mcedit.net) to create a starter platform.

####Flat World Generator Options

The flat world generator options string consists of four parts: `version;blocks;biome;structures` The only thing you should change from the void world settings is the biome.

    #	Biome
    0	Ocean
    1	Plains
    2	Desert
    3	Extreme Hills
    4	Forest
    5	Taiga
    6	Swampland
    7	River
    8	Hell (Nether)
    9	Sky (End)
    10	Frozen Ocean
    11	Frozen River
    12	Ice Plains
    13	Ice Mountains
    14	Mushroom Island
    15	Mushroom Island Shore
    16	Beach
    17	Desert Hills
    18	Forest Hills
    19	Taiga Hills
    20	Extreme Hills Edge
    21	Jungle
    22	Jungle Hills
    
Copied from: [minecraft wiki - BiomeIDs ![](./images/External-Link.png)](http://www.minecraftwiki.net/wiki/Data_values#Biome_IDs)  
