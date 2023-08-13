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
  
![LetsGo](https://github.com/forsbergsskola-se/302-specialization-track-nice1stu/assets/112468923/5bd56274-5723-4bb9-b0f0-a082af2e09c7)

Using pre-rigged character and animations downloaded from Mixamo, replaced the Unreal Manniquin with new mesh. Then created Animation Blueprint to enable character to switch between animations.  
  
![BP_Locomotion](https://github.com/forsbergsskola-se/302-specialization-track-nice1stu/assets/112468923/32a5a7c6-ca1a-4b96-b34d-9644cfd5c332)  

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
