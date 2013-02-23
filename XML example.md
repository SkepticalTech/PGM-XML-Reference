##![](./images/logo.png)[Example XML](id:pageTop)
***



###Race For Victory 2 XML

    <?xml version="1.0"?>
    <map proto="1.3.0">
    <name>Race for Victory 2</name>
    <version>1.2.4</version>
    <objective>Take the enemy's wool located to either side of the enemy's base and place it in your victory monument.</objective>
    <authors>
        <author contribution="map design">Plastix</author>
        <author contribution="map design">IM_A_H0B0</author>
        <author contribution="map design and gameplay management">MonsieurApple</author>
        <author contribution="map design and item management">Anxuiz</author>
    </authors>
    <rules>
        <rule>Players may not obstruct the majority of the lane with lava.</rule>
        <rule>Players may not use lava to block a team's spawn.</rule>
    </rules>
    <teams>
        <team color="blue" max="32">Blue Team</team>
        <team color="dark red" max="32">Red Team</team>
    </teams>
    <spawns>
        <spawn team="blue" yaw="0"><cylinder base="0.5,4,-54.5" radius="2.5" height="0"/></spawn>
        <spawn team="red" yaw="180"><cylinder base="0.5,4,69.5" radius="2.5" height="0"/></spawn>
        <default yaw="270"><cylinder base="44.5,8,7.5" radius="4" height="0"/></default>
    </spawns>
    <filters>
        <filter name="only-blue" parents="deny-players deny-world">
            <allow><team>blue</team></allow>
        </filter>
        <filter name="only-red" parents="deny-players deny-world">
            <allow><team>red</team></allow>
        </filter>
    </filters>
    <regions>
        <!-- blue wool room protection (these are the wools blue has to get) -->
        <union name="blue-wool-rooms">
            <rectangle name="purple-room" min="5,119" max="17,134"/>
            <rectangle name="yellow-room" min="-16,119" max="-4,134"/>
        </union>
        <apply block="only-blue" use="only-blue">
            <region name="blue-wool-rooms"/>
        </apply>
        <apply enter="only-blue" message="You may not enter your own wool room!">
            <region name="blue-wool-rooms"/>
        </apply>
    
        <!-- red wool room protection (these are the wools red has to get) -->
        <union name="red-wool-rooms">
            <rectangle name="orange-room" min="5,-119" max="17,-104"/>
            <rectangle name="lime-room" min="-16,-119" max="-4,-104"/>
        </union>
        <apply block="only-red" use="only-red">
            <region name="red-wool-rooms"/>
        </apply>
        <apply enter="only-red" message="You may not enter your own wool room!">
            <region name="red-wool-rooms"/>
        </apply>
    
        <!-- void protection -->
        <apply block-place="deny-all" message="You may not place blocks in the void!">
            <!-- blue side -->
            <rectangle min="-4,-oo" max="5,-69"/>
            <rectangle min="17,-oo" max="100,-19"/>
            <rectangle min="-16,-oo" max="-100,-19"/>
            <!-- red side -->
            <rectangle min="-4,84" max="5,oo"/>
            <rectangle min="-100,34" max="-16,oo"/>
            <rectangle min="17,34" max="100,oo"/>
        </apply>
    
        <!-- supply room protection -->
        <apply block="deny-all" message="You may not break or place blocks in the storage room!">
            <cuboid name="blue-storage-room" min="-14,0,-65" max="15,9,-41"/>
            <cuboid name="red-storage-room" min="-14,0,56" max="15,9,80"/>
        </apply>
    </regions>
    <playable>
        <rectangle min="-24,-127" max="25,142"/>
    </playable>
    <maxbuildheight>30</maxbuildheight>
    <wools team="red">
        <wool color="orange"><block>-1,5,78</block></wool>
        <wool color="lime"><block>1,5,78</block></wool>
    </wools>
    <wools team="blue">
        <wool color="purple"><block>-1,5,-64</block></wool>
        <wool color="yellow"><block>1,5,-64</block></wool>
    </wools>
    <itemremove>
        <item>string</item>
        <item>glowstone dust</item>
        <item>apple</item>
        <item>sapling</item>
        <item>sugar cane</item>
    </itemremove>
    </map>
    


###Soviet Mills XML

    <?xml version="1.0"?>
    <map proto="1.3.0">
    <name>Soviet Mills</name>
    <version>1.2.1</version>
    <objective>Destroy 75% of the team's spherical monument.</objective>
    <authors>
        <author>Eclipsen</author>
        <author>EnarRikardz</author>
    </authors>
    <contributors>
        <contributor contribution="terraforming and gameplay">Anxuiz</contributor>
    </contributors>
    <rules>
    </rules>
    <teams>
        <team color="dark red" max="50">Red Team</team>
        <team color="blue" max="50">Blue Team</team>
    </teams>
    <kits>
        <kit name="spawn">
            <item slot="0">iron sword</item>
            <item slot="1" enchantment="dig speed:7;arrow infinite:1">bow</item>
            <item slot="28" amount="1">arrow</item>
            <item slot="2" enchantment="durability:3;dig speed:1">iron pickaxe</item>
            <item slot="3" amount="32">bread</item>
            <item slot="4" amount="64" damage="1">leaves</item>
            <item slot="5" amount="64" damage="1">log</item>
            <potion duration="10" amplifier="2">heal</potion>
            <potion duration="20">damage resistance</potion>
        </kit>
        <kit name="red" parents="spawn">
            <chestplate color="cd0000">leather chestplate</chestplate>
        </kit>
        <kit name="blue" parents="spawn">
            <chestplate color="0066cc">leather chestplate</chestplate>
        </kit>
    </kits>
    <spawns>
        <spawn team="blue" kit="blue" yaw="270"><cuboid min="-46.5,54,144.5" max="-44.5,54,146.5"/></spawn>
        <spawn team="red" kit="red" yaw="270"><cuboid min="-46.5,54,-178.5" max="-45.5,54,-176.5"/></spawn>
        <default yaw="270"><cylinder base="101,74,-16" radius="4" height="0"/></default>
    </spawns>
    <filters>
        <filter name="deny-ice">
            <deny><block>ice</block></deny>
        </filter>
    </filters>
    <regions>
        <!-- protect spawn buildings -->
        <apply block="deny-all" message="You may not modify the spawn buildings">
            <cuboid name="blue-spawn-building" min="-50,52,132" max="-41,62,150"/>
            <cuboid name="red-spawn-building" min="-50,52,-182" max="-41,62,-164"/>
        </apply>
    
        <apply block="deny-all">
            <negative><rectangle name="playable" min="-50,-182" max="50,150"/></negative>
        </apply>
    
        <apply block="deny-ice">
            <region name="playable"/>
        </apply>
    
        <apply block="deny-all" message="You may not build over the battlefield">
            <cuboid min="-50,30,-48" max="50,oo,16"/>
        </apply>
    </regions>
    <destroyables completion="75%" name="Monument">
        <destroyable owner="blue" materials="smooth brick;wool:11">
            <cuboid name="blue-core" min="8,49,115" max="17,58,124"/>
        </destroyable>
        <destroyable owner="red" materials="smooth brick;wool:14">
            <cuboid name="red-core" min="8,49,-156" max="17,58,-148"/>
        </destroyable>
    </destroyables>
    <toolrepair>
        <tool>iron sword</tool>
        <tool>bow</tool>
        <tool>iron pickaxe</tool>
    </toolrepair>
    <itemremove>
        <item>arrow</item>
        <item>leather chestplate</item>
    </itemremove>
    <maxbuildheight>69</maxbuildheight>
    </map>


###Scrap Mettle XML

    <?xml version="1.0"?>
    <map proto="1.3.0">
    <name>Scrap Mettle</name>
    <version>1.4.0</version>
    <objective>Score points by killing the other team and entering your team's goal on the other side.</objective>
    <authors>
        <author>KasiCrafter</author>
    </authors>
    <contributors>
        <contributor contribution="Aesthetics and XML Code">Plastix</contributor>
    </contributors>
    <teams>
        <team color="blue" max="50">Blue Team</team>
        <team color="dark red" max="50">Red Team</team>
    </teams>
    <filters>
        <filter name="only-blue" parents="deny-all">
            <allow><team>blue</team></allow>
        </filter>
        <filter name="only-red" parents="deny-all">
            <allow><team>red</team></allow>
        </filter>
    </filters>
    <regions>
        <apply enter="only-blue" message="You may not score in your own goal.">
            <cuboid name="blue-score-protect" min="16,8,-36" max="33,12,-33"/>
        </apply>
    
        <apply enter="only-blue" message="THIS door is BLUES only.">
            <cuboid name="blue-right-trench-protect" min="8,10,135" max="13,13,140"/>
            <cuboid name="blue-left-trench-protect" min="36,10,135" max="41,13,140"/>
            <cuboid name="blue-left-near-base-protect" min="46,10,212" max="49,12,213"/>
            <cuboid name="blue-right-near-base-protect" min="0,10,212" max="3,12,213"/>
        </apply>
        
        <apply enter="only-red" message="You may not score in your own goal.">
            <cuboid name="red-score-protect" min="16,8,228" max="33,12,231"/>
        </apply>
    
        <apply enter="only-red" message="THIS door is REDS only.">
            <cuboid name="red-right-trench-protect" min="36,10,55" max="40,12,60"/>
            <cuboid name="red-left-trench-protect" min="8,10,55" max="12,12,60"/>
            <cuboid name="red-left-near-base-protect" min="0,10,-18" max="3,12,-17"/>
            <cuboid name="red-right-near-base-protect" min="46,10,-18" max="49,11,-17"/>
        </apply>
        
        <apply block="deny-all">
            <rectangle name="playable" min="-11,-56" max="61,251"/>
        </apply>
    </regions>
    <portals>
        <!-- portals from score zones to bases -->
        <portal y="7" z="281" filter="only-blue">
            <cuboid name="blue-score-zone" min="16,8,-36" max="33,9,-35"/>
        </portal>
        <portal y="7" z="-281" filter="only-red">
            <cuboid name="red-score-zone" min="16,8,230" max="33,9,231"/>
        </portal>
        
        <!-- portals from one side to the other through emergency exits -->
        <portal x="-64">
            <rectangle min="57,-oo" max="oo,oo"/>
        </portal>
        <portal x="64">
            <rectangle min="-oo,-oo" max="-8,oo"/>
        </portal>
        
        <!-- red center emergency exits -->
        <portal x="-19" z="1" yaw="180">
            <cuboid min="33,2,53" max="35,4,54"/>
        </portal>
        <portal x="19" z="1" yaw="180">
            <cuboid min="14,2,53" max="16,4,54"/>
        </portal>
        
        <!-- blue center emergency exits -->
        <portal x="-19" z="-1" yaw="180">
            <cuboid min="33,2,141" max="35,4,142"/>
        </portal>
        <portal x="19" z="-1" yaw="180">
            <cuboid min="14,2,141" max="16,4,142"/>
        </portal>
    </portals>
    <kits>
        <kit name="spawn">
            <item slot="0">stone sword</item>
            <item slot="1">bow</item>
            <item slot="28" amount="16">arrow</item>
            <item slot="2" amount="64">cooked beef</item>
            <item slot="3" damage="8229">potion</item> <!-- potion of instant health 2 -->
            <item slot="4" damage="8229">potion</item> <!-- potion of instant health 2 -->
            <item slot="8" amount="1">iron ingot</item> <!-- the scrap metal of Scrap Mettle -->
            <item slot="35" amount="1">stick</item> <!-- given in order to make swords -->
            <potion duration="5">heal</potion>
            <potion duration="10">damage resistance</potion>
            <potion duration="15" amplifier="2">speed</potion>
        </kit>
        <kit name="red" parents="spawn">
            <helmet color="cd0000">leather helmet</helmet>
            <chestplate color="cd0000" enchantment="protection projectile:2">leather chestplate</chestplate>
            <leggings color="cd0000">leather leggings</leggings>
            <boots color="cd0000" enchantment="protection fall:2">leather boots</boots>
        </kit>
        <kit name="blue" parents="spawn">
            <helmet color="0066cc">leather helmet</helmet>
            <chestplate color="0066cc" enchantment="protection projectile:2">leather chestplate</chestplate>
            <leggings color="0066cc">leather leggings</leggings>
            <boots color="0066cc" enchantment="protection fall:2">leather boots</boots>
        </kit>
    </kits>
    <spawns>
        <spawn team="blue" kit="blue" yaw="180"><cuboid min="5,14,237" max="44,14,242"/></spawn>
        <spawn team="red" kit="red" yaw="0"><cuboid min="5,14,-47" max="44,14,-43"/></spawn>
        <default yaw="90"><cylinder base="25,26,97.5" radius="5" height="0"/></default>
    </spawns>
    <score>
        <time>900</time> <!-- 15 minutes -->
        <!-- "Left" and "Right" relative to looking TOWARDS spawn's back wall. -->
        <box value="3" filter="only-blue"><cuboid name="blue-score-zone-left" min="16,8,-36" max="22,10,-35"/></box>
        <box value="3" filter="only-blue"><cuboid name="blue-score-zone-right" min="27,8,-36" max="34,10,-35"/></box>
        <box value="5" filter="only-blue"><cuboid name="blue-score-zone-center" min="23,8,-36" max="26,10,-35"/></box>
    
        <box value="3" filter="only-red"><cuboid name="red-score-zone-left" min="27,8,230.5" max="34,10,231"/></box>
        <box value="3" filter="only-red"><cuboid name="red-score-zone-right" min="16,8,230.5" max="22,10,231"/></box>
        <box value="5" filter="only-red"><cuboid name="red-score-zone-center" min="23,8,230.5" max="26,10,231"/></box>
    </score>
    <toolrepair>
        <tool>stone sword</tool>
        <tool>bow</tool>
    </toolrepair>
    <itemremove>
        <item>leather helmet</item>
        <item>leather chestplate</item>
        <item>leather leggings</item>
        <item>leather boots</item>
        <item>iron sword</item>
        <item>iron spade</item>
        <item>iron pickaxe</item>
        <item>iron axe</item>
        <item>iron hoe</item>
        <item>iron helmet</item>
        <item>iron chestplate</item>
        <item>iron leggings</item>
        <item>iron boots</item>
        <item>glass bottle</item>
        <item>minecart</item>
        <item>rails</item>
        <item>cauldron</item>
        <item>iron door</item>
        <item>bucket</item>
        <item>shears</item>
        <item>iron fence</item>
        <item>cooked beef</item>
        </itemremove>
    </map>




####XML Info

* What is XML? [Introduction to XML ![](./images/External-Link.png)](http://www.w3schools.com/xml/xml_whatis.asp)
* See [maps.oc.tc ![](./images/External-Link.png)](https://maps.oc.tc) for XML file examples.
* The XML files should be run through a XML validator before being submitted.
* XML files should also be correctly indented to improve readability.


### [Go to Top](#pageTop)

*Last edited: February 8, 2013*
