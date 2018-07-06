Maps in EQEmu are used to do many things, we have different files that are responsible for different functions

# File Structure

* maps/base/zoneshortname.map
* maps/nav/zoneshortname.nav
* maps/water/zoneshortname.wtr
* maps/path/zoneshortname.path

### Water Maps (.wtr)

* Water maps are responsible for one if not obvious, determining whether or not a client is inside water. Server side we determine different combat logic and pathing logic when a mob and/or client is in the water
* Water maps takes a point (x, y, z) and determines what type of region said point is marked as eg water, lava, normal

### Navigation Mesh (.nav)

* Navmesh is modern navigation mesh technology, we use it server side to determine shortest path to a target in NPC AI decision making processes, it's what the server uses to determine what NPC's can walk on and they will strictly adhere to this mesh when making pathing decisions
* Example of this in game: https://www.youtube.com/watch?v=ujtqipXAP1E

***

Here is another explanation taken from [Stack Overflow](https://gamedev.stackexchange.com/a/15395)

* It is same as waypoint pathfinding, only instead of way-points you have way-polygons and You can infer few things about navmesh from it:

* way-polygons are areas where entities can safely walk
  * other areas should probably be not considered
  * way-points need to do leap of faith into space between them; remember NPCs stucking in walls? It was at places where two waypoints were not directly connected.
* There is potentially less nodes (because polygons are biger)
  * Therefore it is most likely faster
  * Therefore it has potentially smaller memory requirements
* It is more realistic (because polygon's area contains in theory infinite amount of points)
  * At polygons You might do some flocking behaviour to avoid collisions between NPCs