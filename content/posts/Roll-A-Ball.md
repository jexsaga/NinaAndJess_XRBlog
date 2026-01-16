+++
date = '2025-12-02T11:00:44+01:00'
draft = false
title = 'Lab 2 : Roll-A-Ball'
+++

In this project we learned the basics of using Unity. We followed the tutorial which showed us the structure of VR projects along with how to insert objects into the world. 

**1 SETTING UP THE GAME**
-
In seeting up the project, we experienced difficulty in getting the correct versions on our individual computers. After getting Unity to work we added the very first objects, like walls, floor and player.

**2 MOVING THE PLAYER**
-
In this part, we added a Rigidbody to the Player sphere, using physics engine, we wrote our first script in C# to make the sphere roll using the keyboard.

[MOVING THE PLAYER Screenshot](/NinaAndJess_XRBlog/images/rollaball2.mp4)

**3 MOVING THE CAMERA**
-
Next, we set the camera position, and used a script to make the Camera follow the Player with a fixed offset.

[MOVING THE CAMERA Screenshot](/NinaAndJess_XRBlog/images/rollaball3.mp4)

**4 SETTING UP THE PLAY AREA**
-
After, we configured the play area for the game with walls.

[SETTING UP THE PLAY AREA Screenshot](/NinaAndJess_XRBlog/images/rollaball4.mp4)

**5 CREATING COLLECTIBLES**
-
To create collectibles, we first created a PickUp GameObject for the player to collect, then wrote a script to rotate the collectibles. We used prefab to create more collectibles and make the modifications of them easier.

[CREATING COLLECTIBLES Screenshot](/NinaAndJess_XRBlog/images/rollaball6.mp4)


**6 DETECTING COLLISIONS WITH COLLECTIBLES**
-
We, of course, needed to make sure the collectibles were actually collectable, so we revised our PlayerController script to make the collectibles disappear when they collide with the Player sphere. 
We used tags and conditionnel statements to make sure they're the only things that disappear, then we set the Prefab PickUp Collider as a trigger and added a RigidBody component to make the collectibles work properly.

[DETECTING COLLISIONS WITH COLLECTIBLES Screenshot](/NinaAndJess_XRBlog/images/rollaball9.mp4)


**7 DISPLAYING SCORE AND TEXT**
-
To make the game understandable and feel like a game, we created a counter to score the value of collected PickUp GameObjects.
With that, we created and configured UI Text Element to display the count value and an end of game message.

[DETECTING COLLISIONS WITH COLLECTIBLES Screenshot](/NinaAndJess_XRBlog/images/rollaball10.mp4)

**8 ADDING AI NAVIGATION**
-


rollballlafinnnnn.mp4
+++
date = '2025-12-02T11:00:44+01:00'
draft = false
title = 'Lab 2 : Roll-A-Ball'
+++

In this project we learned the basics of using Unity. We followed the tutorial which showed us the structure of VR projects along with how to insert objects into the world. 

**1 SETTING UP THE GAME**
-
In setting up the project, we experienced difficulty in getting the correct versions on our individual computers. After getting Unity to work we added the very first objects, like walls, floor and player.

**2 MOVING THE PLAYER**
-
In this part, we added a Rigidbody to the Player sphere, using physics engine, we wrote our first script in C# to make the sphere roll using the keyboard.

[MOVING THE PLAYER Screenshot](/NinaAndJess_XRBlog/images/rollaball2.mp4)

**3 MOVING THE CAMERA**
-
Next, we set the camera position, and used a script to make the Camera follow the Player with a fixed offset.

[MOVING THE CAMERA Screenshot](/NinaAndJess_XRBlog/images/rollaball3.mp4)

**4 SETTING UP THE PLAY AREA**
-
After, we configured the play area for the game with walls.

[SETTING UP THE PLAY AREA Screenshot](/NinaAndJess_XRBlog/images/rollaball4.mp4)

**5 CREATING COLLECTIBLES**
-
To create collectibles, we first created a PickUp GameObject for the player to collect, then wrote a script to rotate the collectibles. We used prefab to create more collectibles and make the modifications of them easier.

[CREATING COLLECTIBLES Screenshot](/NinaAndJess_XRBlog/images/rollaball6.mp4)


**6 DETECTING COLLISIONS WITH COLLECTIBLES**
-
We, of course, needed to make sure the collectibles were actually collectable, so we revised our PlayerController script to make the collectibles disappear when they collide with the Player sphere. 
We used tags and conditionnel statements to make sure they're the only things that disappear, then we set the Prefab PickUp Collider as a trigger and added a RigidBody component to make the collectibles work properly.

[DETECTING COLLISIONS WITH COLLECTIBLES Screenshot](/NinaAndJess_XRBlog/images/rollaball9.mp4)


**7 DISPLAYING SCORE AND TEXT**
-
To make the game understandable and feel like a game, we created a counter to score the value of collected PickUp GameObjects.
With that, we created and configured UI Text Element to display the count value and an end of game message.

[DETECTING COLLISIONS WITH COLLECTIBLES Screenshot](/NinaAndJess_XRBlog/images/rollaball10.mp4)

**8 ADDING AI NAVIGATION**
-
At the end, we implemented a NavMesh for AI-based enemy navigation, added static and dynamic obstacles to challenge the player, and code win and lose conditions using Unity scripting. 

We encountered some problems during the initial implementation, as the enemy would pass through walls and remain at distance from the player while continuing to follow them. We tried implementing RigidBody, which helped but didn't solve the problem. So we followed the tutorial entirely again, and it worked. We assumed that the connexion between the enemy and some properties was not configured right.

[ADDING AI NAVIGATION Screenshot](/NinaAndJess_XRBlog/images/rollballlafinnnnn.mp4)

