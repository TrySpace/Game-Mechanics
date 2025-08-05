# Edge Offset

Jumping offset; the threshold the ability to jump has, is not straight down,
but has a radius and a diagonal array around the player.
This way jumping has a certain tolerance in its timing, when jumping later, the distance the jump goes will be calculated from the outmost jumping-off point, as if the played had timed it perfectly, thus the jumping trajectory is retro-calculated to be the maximum within a certain time/distance from the edge.
This allows a player to jump earlier and jump shorter, but jump later and be always the same jump-off point, thus encouraging pressing jump later rather than too early.

## Diagonal tolerance
The edge of the jump can be more lenient when the edge is more than 90 degrees down; i.e. a sloping edge gives more leeway for jumping later.

