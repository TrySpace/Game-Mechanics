A more natural, forgiving, and less frustrating jumping mechanic.

# Edge Offset

The jump detection area extends beyond the exact edge, creating a tolerance zone around the player. This allows for timing forgiveness - jumping later within this zone still results in the optimal jump trajectory, as if the player had timed it perfectly.

## Benefits
- Players can jump early (shorter distance) or late (optimal distance)
- Encourages precise timing without punishing slight mistakes
- Reduces frustration from edge detection issues

## Diagonal Tolerance
Sloped edges (greater than 90° downward) provide additional timing leniency for late jumps.

## Beyond the tolerance zone
Past the tolerance zone, jump power decreases based on edge type. Sharp edges are least forgiving, sloped edges more forgiving.

### Vertical tolerance
If the jumper is still close enough to a vertical surface down from the edge, a jump may still be possible, depending on the material. The jump trajectory will however be a combination of the players momentum and the avarage surface angle of the jumping contact point.

## Multiple jumps
There is no limit to jump initiations after leaving the last stable ground.