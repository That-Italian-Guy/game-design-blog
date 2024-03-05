---
title: "Building prefabs with Dungeon Alchemist & Foundry VTT"
date: 2024-01-16
excerpt: Leverage the Procedural Generation in Dungeon Alchemist to quickly create the base for prefab buildings in Foundry VTT that can be added to any battlemap.
toc: true
header:
  teaser: /assets/images/video-blogs/banner_da_prefab1_001.webp
categories: 
  - vtt
tags:
  - video
  - vtt
  - foundry
  - dungeon alchemist
  - tutorial
---

{% include video id="hFTiLF6oifc" provider="youtube" %}

{% capture notice-text %}
- [Better Roofs module](https://github.com/theripper93/Better-Roofs/)
- All the assets for this prefab can be found here: [Images](https://imgur.com/a/CV7uDqV), [JSON file](https://pastebin.com/J5XZWd3f)
- Free assets from [Forgotten Adventures](https://www.forgotten-adventures.net)
- Music: [Bensound](https://www.bensound.com)
- [Advanced Prefabs #1](https://youtu.be/4e9xosxoBu0)
- [Advanced Prefabs #2](https://www.youtube.com/watch?v=ewHXyRNDnxo)
- Prefab credit to [Baileywiki](https://www.youtube.com/channel/UCg6hyng0ObRKLwfz3QIhcog)
{% endcapture %}
<div class="notice--info">
  {{ notice-text | markdownify }}
</div>

## Text Version
In this tutorial we will leverage the Procedural Generation in Dungeon Alchemist to quickly create the base for prefab buildings in Foundry VTT that can be added to any battlemap. All the assets for this prefab are linked above!
## Create the map in Dungeon Alchemist.
+ Generate any map you want in Dungeon Alchemist. 
  + In this case, we are creating a Tavern.

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_001.webp" caption="Our procedurally generated Tavern." %}

+ Export it as a Foundry VTT map.
+ In this example, I'll export it as 72 DPI. Export the "map" with Ortographic (top down) Perspective.
+ You can use but you can choose 100 or 150 DPI if you want your images to be sharp, but be mindful about your player's bandwidth!
  + Make sure you are exporting your map with a DPI that matches the pixel size of the grid you are going to use in Foundry VTT!

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_002.webp" caption="I prefer to export gridless in DA" %}

## Edit the map in a Photo Editor
+ Open the image for the map you have exported in your preferred Photo editor (in this case Photoshop). 
+ Use a combination of Magic Wand and free selection to select everything in the "Dark Parchment" background area.
+ You can refine your selection with the rectangular marquee:
 + In Photoshop, use Shift + Click to add to your selection or Alt + Click to remove.

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_003.webp" caption="Refining the selection." %}

+ Invert your current selection.
+ Copy the new selection.
+ Create a new file and Paste your clipboard's content. 
+ Crop the image so that it only contains your building (and its shadow) and remove the white background.
+ Using a combination of Magic Wand and free selection, select the dark shadows
+ Cut them and Paste them into a new Layer. 
+ Reduce the Fill for that level to 33%. It'll look like this:

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_004.webp" caption="Building with transparent shadow." %}

+ Make sure to save the image as a .PNG (we need the transparency)!

## Create the base building in Foundry VTT
+ In Foundry VTT, open up your World and create a new Scene (the name doesn't matter). 
+ Right click on the Scene in the right bar and select Import Data. 
+ Select the .JSON file generated by Dungeon Alchemist.
+ This Scene now has all the details for our building (aside from the map itself):

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_005.webp" caption="Imported map with walls and lights." %}

+ Create a new Tile and modify its width and height to match the ones of the .png file you have worked with in your Photo Editor.
+ Add the .png image to the tile.
+ Click Update Tile.

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_006.webp" caption="A tile displaying our Tavern" %}

+ Line up your Tile with the existing Walls. 
 + You can use the Shift key while moving the tile around to avoid the snap-to-grid effect if needed.

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_007.webp" caption="Looking good!" %}

+ Once you are satisfied with the position, create a new Tile
+ Add the Roof the same way. 
  + You may have to resize your Roof so that it overextends slightly over the walls - it'll look better when someone walks inside!
  + Click the "Overhead Tiles" button and use the walls to properly line up your roof.

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_008.webp" caption="Tiles and walls are displayed at the same time" %}

## Create a Prefab of the building
+ For this to work at all, you'll need the [Token Attacher mod](https://foundryvtt.com/packages/token-attacher/) for Foundry.
+ In Foundry VTT, click and drag a blank Token onto the Scene, next to your building. Give it a fitting name.

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_009.webp" caption="Prefab-Token it is." %}

+ With the Token selected, open the Attaching UI from Token Attacher.
+ This will display a new popup side menu that we will use to link our different parts together.

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_010.webp" caption="The Attaching UI." %}

+ Click and drag to select our building AND the token.
  + Make sure to have a wide enough selection to include all the (non displayed) walls and lights too!
+ After this, the Token will be attached to your building - when you move it around, everything (map, walls, lights) will be moved together with it.
+ Create a new NPC Actor.
+ Name it something appropriate and assign it the building's map as its art. Click "Prototype Token".

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_011.webp" caption="Our Prefab-Tavern Actor." %}

+ Making sure you have the token selected, click "Assign Token".

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_012.webp" caption="Assigning the Token to our Actor." %}

+ This will assign all the values for the selected token (including all the information from Token Attacher) to the default Token for our Prefab-Tavern Actor.
+ Our prefab is now an actor whose token can be click-and-dragged to any battlemap like any other NPC.
+ It will be instantly recognizable as a specific building from the art we have assigned to it.
+ Here you can see the same prefab "imported" into a different Scene:

{% include figure image_path="/assets/images/video-blogs/da_prefab1/da_prefab1_013.webp" caption="Everything working as intended." %}

{% capture notice-text2 %}
**I want more prefabs tips!**
If you are ready more advanced prefabs - with hot-swappable art assets, multi-level and with automated transitions - check out these two videos! 
{% endcapture %}
<div class="notice--info">
  {{ notice-text2 | markdownify }}
</div>

{% include video id="4e9xosxoBu0" provider="youtube" %} {% include video id="ewHXyRNDnxo" provider="youtube" %}