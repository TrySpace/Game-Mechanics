# Time-loops with past versions of self
A timeloop where you encounter your past self

## Time bubbles
Past versions of you or your actions are contained in an impenetrable bubble to preserve the timeline.

### Changing the past
A mechanic allows you to enter a time-bubble and trigger a re-do event. You make changes, which affect the timeloop, then exit the bubble at the same position to keep the rest of the timeline intact.
So version A of you goes from position X to Y, then the next loop version B comes by and interferes with A and makes him go from X to Z. After that the player is forced to re-do and play as A again and make sure he ends at Y instead of Z.

## Caveats and Paradox Prevention

### Bubble Resolution Paradox
The primary paradox risk occurs when a time bubble's interference creates a situation where the bubble can never be resolved to reach the original consequence. For example, if version B's interference with version A creates a state where A can no longer reach position Y, the timeline becomes impossible.

**Solution**: Implement a "resolution validation" system that checks if the current bubble state can still lead to the required outcome. If resolution becomes impossible, the game can either:
- Force a re-do with a clear explanation of what made the goal unreachable
- Provide hints about what actions would restore the path to the required outcome
- Allow the player to "reset" the bubble to a previous state within the same loop

### State Contradiction
When version B's interference creates a game state that logically conflicts with version A's required path. For example, if B removes a key that A needs to reach position Y.

**Solution**: Use a "path validation" system that tracks whether version A's required actions are still possible after B's interference. If contradictions are detected, the game can:
- Highlight the specific obstacle preventing A from reaching the goal
- Suggest alternative approaches that would restore A's path
- Force a re-do if the contradiction makes the goal impossible
- Some required 'canonical' objects like a key cannot be removed

### Intentional Infinite Loops
Players might purposefully create endless loops to exploit game mechanics or avoid consequences.

**Solution**: Implement a "loop efficiency" system that:
- Tracks the number of loops needed to reach the same goal
- Rewards players for achieving goals in fewer loops
- Provides diminishing returns for repeated identical actions
- Could introduce "loop fatigue" where excessive looping reduces effectiveness
- Possibly auto-resolve loop issues by autopathing the player to Y when not resolved 100% at the end of re-do event.

### Performance Considerations
Storing time bubble states and tracking resolution paths can become memory-intensive.

**Solution**:
- Limit the number of active time bubbles
- Implement state compression for older bubble states
- Use "checkpoint" systems where only key decision points are preserved
- Consider a "bubble decay" system where very old bubble states are simplified

