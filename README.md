This is a page dedicated to documenting and explaining features and works of Minecraft’s custom world-gen. This will also include helpful links and tutorials on important things.
## Important links
[Minecraft wiki page on custom world-gen](https://minecraft.gamepedia.com/Custom_world_generation)

[Aelve’s imitation of vanilla_layered](https://www.planetminecraft.com/data-pack/imitation-of-vanilla-layered-with-multi-noise-experimental/)

[Data-pack World-gen discord](https://discord.gg/J49Rwnz)

[Slicedlime’s reference files](https://github.com/slicedlime/examples)


## Tutorials

## How to make a basic biome
Biomes in datapacks use basic json syntax, so I would suggest learning json beforehand(watch this basic json tutorial). 
For this tutorial we will be modifying one of slicedlime’s reference files, since these files have very specific  this is usually the easiest way to make biomes. 
## How to use Aelve’s imitation of vanilla_layered
Essentially the main biomes lie on a 2D grid using odd-numbered temperature and humidity values. Each of these biomes alternates in and on/off pattern between a weirdness value of 0.09 and 0.11. 

If your added biomes don't follow this pattern, you can't add rivers (or at least the rivers won't look good).

To put a river between two biomes, you put the river's values halfway between the two biomes. You can realistically only add rivers between neighbouring biomes in the grid. There is a graph showing where each biome is located in a .xlsx(excel) file.

As an example:
```json
{
  "parameters": {
    "temperature": 0.3,
    "humidity": -0.3,
    "altitude": 0.5,
    "weirdness": 0.11,
    "offset": 0.0
  },
  "biome": "minecraft:desert"
},

// Between desert & savanna
{
  "parameters": {
    "temperature": 0.4,
    "humidity": -0.3,
    "altitude": 0.5,
    "weirdness": 0.1,
    "offset": 0.095
  },
  "biome": "minecraft:river"
},

{
  "parameters": {
    "temperature": 0.5,
    "humidity": -0.3,
    "altitude": 0.5,
    "weirdness": 0.09,
    "offset": 0.0
  },
  "biome": "minecraft:savanna"
},```
The rivers have an offset value, but I haven't found a pattern with them. It just requires trial and error to get right.

When adding new biomes some things to keep in mind for noise values:

> "temperature" and "humidity" are the main way of controlling where in relation to the other biomes the new one will generate. Almost all land biomes fall on this 2D grid. An exception is jungles, which use altitude. The values generally follow what you would expect of the names (to a degree); deserts are hot and dry, forests are hot and humid, etc.

> "altitude" mostly controls oceans. It is also used for islands and the jungle.

> "weirdness" controls coastlines and rivers. Each biome alternates in an on/off pattern of 0.9,0.11 weirdness to mitigate straight lines on biome borders. When adding a biome check to see what biome it is next to and use the other value. All rivers lie on a weirdness value of 0.1.

>"offset" has no common features. Use this to make biomes smaller and rarer.



