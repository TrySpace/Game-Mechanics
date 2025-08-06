# Main goal
The main purpose is to have a fully simulated state of entities at a large scale. Mainly so that if a player interferes that realistic cascading consequences of their actions can be calculated in the least performance-heavy way possible.

# City-Block Simulation
A metropolitan city block, possibly with more streets than 4; With at least 1 tall office building or sky-scraper, with different types of businesses on different floors. Some restaurants, food-vendors, coffee-shops etc. are on the block, and the rest are residential buildings.
The idea is that the simulation is isolated and the whole block is self-sustaining, but it could be scaled up to a whole city size where everything and everyone is interconnected, but simulated in a simplified and predetermined way, until the player interferes with something.

## Interference
When the player interferes with a moving entity a new trajectory is calculated, in the most simple case this means a delay is added to an NPCs schedule and routing. They might walk faster to catch up, take a cab instead of the train, or call in sick, depending on the circumstance of the interference.
There is a limited set of consequences or interference an entity (NPC or object) can have, in order to simplify and limit calculative impact:
- Location (XYZ)
- Speed (v)
- Aliveness/Operability (%)
- Specific states:
  - Emotional state
  - Relational state
  - Specific objective states
Any part of the simulation that is unaffected will not need to be simulated as much as realtime, as it will just be a chronological list of actions to follow.

## Simulation
The simulation should be savable in whatever state it is currently in in order to save/load it.
A simplified 2d grid with a z axis for height (thus a 3d matrix) is used to simulate entities. It has a lower resolution than the rendered models in-game for precision.
The rendered locations of the entities in engine is calculated between the coordinates that the simulation dictates.

Each entity has a vector calculated from their last location.
Entities in-game will only be rendered within a certain range or vision cone. More distant entities are rendered on a lower tick. (See # Local Simulation)

The main goal is to generate a precalculated simulation where no-one has to painstakingly coordinate and manually place NPCs around the city and give each a job and path; the simulation generator would manage this with the help of designated job spaces and home areas.

# Generation
The city might be manually designed by people, or dynamically/AI generated, but instead of assigning thousands, to even millions of NPCs, the designer/AI would assign certain spaces as workplaces and others as homes, and others as public spaces like restaurants, cafes, etc. The simulation generator would then determine a logical, sensible and realistic distribution of jobs, job types and which people would work where. The designated areas would be dynamically generated but can also be manually assigned by the designers and tweaked for finetuning.
Specific pathing will not be generated, since only large scale pathing is relevant. A path from home to work will be simplified to the connecting road, and is assumed to be accessible.
When a path becomes inacessible all relevant pathings intersecting with the path will be recalculated, and these calculations will be executed in order of proximity as to not overload the main thread. So it will prioritize the local simulations visible impact first.
## Interior Spaces
Homes, apartments and offices would not all be specifically designed, but certain prefabs prototypes are made of which variations can be generated. It will however be pre-generated so nothing is generated on the spot and every interior will always be consistent and pure to the paramenters they are given. Most homes would be generated together with the NPC personality type, background and current job/income level in mind.

## Entities
Several types of tracked entities
- Living
  - People (NPCs)
  - Animals (Dogs, Cats, Rats, Pigeons)
- Transport
  - Cars
  - Elevators
- Items
  - Groceries
  - Furniture

# Living entities

## NPCs
### Backgrounds
Background distributions like education, their origin sotry, if they are local or not etc will be generated alongside their personality profiles.
### Personalities
A set of personality traits pre-determines NPCs general decisions like what they buy, what they eat for lunch or what they do on their breaks. About 90% of NPCs will on a 9 to 5 job and have very similar overall behavior. When they get home or when they wake up are the times their personality will show most.
The other 10% would be more handcrafted or have more specific jobs like, managers, CEOs, or homeless people or buskers. About 70% would work in offices, the others 20% in smaller buildings doing more specific jobs like food service, DMV or a clinic or yoga-practice to name a few.
### Relationships
NPCs will have a limited set of relationships like family, friends and coleagues, which can be affected by circumstances that the player causes.

### Pathing
Entities will have a set schedule and itinerary for each day, and will determine their path finding. Most path finding is precalculated since many NPCs will share a route and take the shortest route depending on their personality profile and circumstances.

## Transport
Vehicles will have their ownerships and will be moved around contextually.

## States

## Transport
Cars will be limited in a city, as not everyone will have a car, and most NPCs will take public transport or walk depending on distance.
Parking spaces will be assigned to people in the generation phase to reduce dynamic possibility cascades concerning spacing. Most parking spaces will be in carparks, or at the side of roads, and many traffic will be business related like transport/supply and professional services like cabs or police patrol etc.


# Local Simulation
Rendered simulation is more complex and is derived from the main simulation.
An NPC coming home might have a conversation with their wife which can depend on what they did that day at work or during their commute etc.
## Interference
Interfering will run a local simulation that will eventually dicate the grand scheme of the main simulation

## Pathing
Local pathing will be based on higher-level goals and routes that the simulation has dictated.

## Crowd Simplification
Crowds of people will have simplified herd behavior to lighten the CPU/GPU load.