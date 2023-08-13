Coin Collector  

Requirements:
Unreal Engine 5.2 C++ exercise creating game mechanics in C++ to spawn actors and add interactor component for actor interaction  

The Spawner

Create an AActor class that will be your spawning actor—use a cube or other primitive component to make it visible.
Make a manager object. Classes that can be used for this include AInfo, UWorldSubsystem, and AGameMode, with varied requirements between the three.
Create a publicly accessible method in the manager object called “Spawn” that takes a FVector as a parameter.
In the manager object, create a private TArray that stores pointers to your spawned object class.
Create an AActor class that will be your spawn point object.
In the spawn point, add a public floating point variable that is the radius of the spawning area.
In the spawn point, add a public integer variable that is the number of spawns that should happen.
Use DrawDebugHelpers to draw a debug circle or sphere on Tick, to visualize where the spawning area is.
In OnBeginPlay, trigger the manager object’s Spawn method at random locations inside the radius the specified number of times.
In the Spawn method in the manager, use SpawnActor or other gameplay function to create a new actor and add it to the TArray of actors each time the Spawn method is called, then move the newly spawned actor to the supplied Location.

The Interactor

Create an ActorComponent that will collect potential interactive objects. Add this to your player.
Create an Interface that has a single method that allows you to interact with any Actor that implements it.
Create an AActor that implements the Interface and add it to the world. (Or add the interface to the spawned AActor from the previous exercise.)
Make the ActorComponent collect possible targets in its TickComponent method. Possible alternatives are using an Overlap (such as GetWorld()->OverlapMultiByChannel) or getting the TArray of actors from the manager object in the previous exercise. You could also use a LineTrace from the player’s camera. Consider the benefits of each method before you implement one. For example, can an AI make use of the LineTrace variant?
Pick the most relevant of the collected possible targets and safely call the interface on that target.
Implement the same interface on a Blueprint actor.

![303SpawnCoins](https://github.com/forsbergsskola-se/303-ue-cpp-CoinCollector-nice1stu/assets/112468923/c6f3ccbb-35b7-41ba-81a4-bb686205657f)

Following on from the initial exercises to create class in C++, and adding components (in this case rotator) to the actor, I progresses then to create a way to spawn the statues (in my case coins) into the scene. This is managed by creating an AInfo class called StatueManager which manages the instantiating of statue actors in the scene. The statueManager class creates the array that stores the all the instances of the coins that are spawned in the scene. In the GameMode class we create an instance of the StatueManager to use it in game. Then we create a SpawnPoint actor which is in the scene. This controls the location at which the statues are spawned in the scene. By making the Location of the SpawnPoint and SpawnRadius we can adjust this in the Unreal Editor directly to affect where and how far statues are spawned in scene. A debug sphere (red) is drawn centred on the Spawnpoint extending to the range of the SpawnRadius to indicate the area at which the coins will be randomly spawned.  

There was a big issue with the way the classes were constructed where the coins were spawning progressively further and further outside of the spawn radius. Debugging showed the issue was with the MoveComponent which took over the spawning of the coins after the coins are initially spawned at BeginPlay. By taking the current location of the coin and adding a randomly generated vector, it led to the coins spawning further and further from the sapwn radius initially set by in the SpawnPoint class, as inidicated by the red debug circle. After much analysis, I fell upon the simple method of creating a global location for the SpawnPoint and SpawnRadius which is use by the SpawnPoint and MoveComponent ensured that the coins did not respawn outside the radius of the SpawnRadius.
  
![303Interactor](https://github.com/forsbergsskola-se/303-ue-cpp-CoinCollector-nice1stu/assets/112468923/dd8025e9-5d71-4204-ae53-2a197fe429c4)



Made use of BlendSpace to enable smoother transition between Idle <-> Walk <-> Run.  

![BS_WalkRun](https://github.com/forsbergsskola-se/302-specialization-track-nice1stu/assets/112468923/fcb55695-396a-480a-9aaf-0d0c5d26acb3)  

Also created a short clip of a blend of anaimations using Anim Montage set to play at Game Over  

![Celebration Montage](https://github.com/forsbergsskola-se/302-specialization-track-nice1stu/assets/112468923/7eb60ef0-5ada-4847-a828-76fe3d3d2c9e)  

Plus: Did add simple sfx on statue collected and background music.  

Link to the Youtube Video  
[![click to watch the video](https://img.youtube.com/vi/9S8uEFoUkgI/maxresdefault.jpg)](https://youtu.be/9S8uEFoUkgI)  

Link to the GitHub Repository:  
https://github.com/forsbergsskola-se/302-specialization-track-nice1stu  

Mission Accomplished !
![Jump4Joy](https://github.com/forsbergsskola-se/302-specialization-track-nice1stu/assets/112468923/f656ab3b-85b6-4b76-8e86-abfb52e2e076)
