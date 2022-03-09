# TiledMapParser
A C++ header for parsing maps from the editor [Tiled](https://www.mapeditor.org/). Comes with [rapidxml](http://rapidxml.sourceforge.net/).

The headers deserialises the Tiled map data into structs that can be used by the rest of your program to extract the map in your game's logic.

#### Note: you will need to change the code inside the comments "CODE THAT YOU NEED TO CHANGE" at the beginning of tiled.h to match your file structure and the custom properties you have set in tiled. (there is some example code already there to show you the structure)


## unsupported Tiled features:

* infinite maps
* ellipse and polygon objects
* Text
* Flipping
* Templates
* objects with a Tile Image

## use

make sure to look at the struct definitions after "CODE THAT YOU NEED TO CHANGE" to see how the data is stored

add "tiled.h" and "rapidxml.hpp" to your project files, and include "tiled.h" where you need to load your maps.

To load a map:
```
map = tiled::Map("mymap.tmx");
```
example of acessing data to add collidable objects:
```
for(const auto &objGroup: map.objectGroups)
{
  for(const auto &obj: objGroup.objs)
  {
    if(obj.props.collidable || objGroup.props.collidable)
      colliders.push_back(glm::vec4(obj.x, obj.y, obj.w, obj.h));
  }
}
```

For a full example of this library being used in a game [check out the code for a map class that uses a loaded map.](https://github.com/NoamZeise/GGJ22/blob/main/src/map.cpp)
