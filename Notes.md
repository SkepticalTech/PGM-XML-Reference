####Notes

* `TODO:` watch a match of Parallax to see how exactly lanes function so I can write a better description.
* Perhaps follow the [wikipedia writing guide ![](./images/External-Link.png)](http://en.wikipedia.org/wiki/Wikipedia:Writing_better_articles) & rewrite the sections that use you or your?
* Document the `<point>` element. See the [Babylon spawns ![](./images/External-Link.png)](https://maps.oc.tc/Babylon/map.xml) for an example.

**Undocumented Commits & Stuff:**

* `af0349` Allow velocity to be set when entering regions.
* Added the ability to specify what dimension a world can be loaded in.
* Score `<limit>` and `<death>` subelement. ???  
`<death>` element specifies the score amount added/subtracted for kills/deaths.  
`<limit>` limits the score, when a team (player?) reaches this score the game ends.

* Added the health and hunger kits.  

      <!--  Min and max values? -->
      <health>20</health>
      <saturation>20</saturation>
      <foodlevel>20</foodlevel>

* Added the hunger module.  
`<hunger>` Does it have a `depletion` subelement?

* Filter `<void>` `<not>` `<one>` `<all>` and `<any>` elements.


Possibly Documented:

* Added the time limit module.
* `3723a38` Implement a customizable cooldown for scoreboxes (default 1 second). 
* Added the ability to limit scores.


<br/>
**Other**

Stolen from [RFV3 ![](./images/External-Link.png)](https://maps.oc.tc/RFV3/map.xml)
Basically what this does is check the specified regions for blocks on the bottom layer of the world. It then creates an outline of those blocks and players can only place blocks inside that outline. Bridges are usually not detected because they are not at `y=0`, PGM should probably squash all `Y` layers into one before creating the outline.

    <filters>
        <filter name="no-void" parents="allow-all">
            <deny><void/></deny>
        </filter>
    </filters>

    <regions>
        <apply block="no-void" message="You may not edit the void area">
            <negative>
             <rectangle min="-14,-12" max="15,13"/>
             <region name="portals"/>
            </negative>
        </apply>
    </regions>
    

#### Symbol Information
`§` Indicates that the previous statement is a logical assumption by the author, and not based on any facts as of when it was written.  
`§` May also indicate that the author is unclear about how the element, tag or attribute works.  
`~` Indicates that the section is incomplete or needs a rewrite.
