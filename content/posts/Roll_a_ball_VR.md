+++
date = '2026-02-04T22:16:25+01:00'
draft = false
title = 'Lab 3 : VR in Unity'
+++

At the beginning of the project, we followed the tutorial directly inside the headset and connected it to Jessica’s Meta account.

We first attempted to follow the tutorial provided in the course slides. However, we were using a more recent version of Unity and our headset model differed slightly from the one used in the tutorial. Because of these incompatibilities, we decided instead to follow an official tutorial specifically designed for the Meta Quest:

https://developers.meta.com/horizon/documentation/unity/unity-tutorial-hello-vr/

The first step was to install a compatible Unity version (6.1 or newer). We selected version 6000.3.1f1 and installed the Android Build Support module. We then added the necessary project assets: Meta XR Core SDK, Meta XR Interaction SDK, Meta XR Simulator, and Meta XR Platform SDK.

When creating the Unity project, we used the Universal 3D template. A significant amount of configuration was required: enabling XR Plug-in Management, selecting the correct build platform, integrating the Meta SDK into the project, and resolving configuration warnings. This stage took considerable time, mainly due to long installation and compilation processes.

Once the setup was complete, the basic VR environment was nearly operational. We added our first elements: a camera rig and a simple grab interaction object (a blue cube) that could be grabbed directly with hand tracking, without using controllers.

We then paired the headset with Jessica’s Meta Horizon account and activated developer mode. Afterward, we connected the headset to Nina’s computer via USB and attempted to run the project.

We spent a long time understanding how to properly deploy the application. The tutorial simply indicated pressing the Play button, which did not work for us, even using Meta Link. After researching online, we realized we had to use the Build and Run option instead. The first build took approximately 25 minutes, but it finally worked.

We then reused this VR setup as the base for implementing the Roll-a-Ball game in virtual reality. We exported the Roll-a-Ball project as a .unitypackage and imported it into the VR environment created during the tutorial.

Unlike what was indicated in the course slides, we did not encounter the expected errors, so no additional fixes were necessary.

We created the scene by adding a large plane as the floor and a box acting as a table, on which we placed the Roll-a-Ball game.

A camera rig was added to represent the player in the virtual world. This rig integrates the VR headset: it defines the player’s forward direction and displays the viewing frustum, allowing us to visualize what the player sees when entering the scene. We configured all required parameters, including tracking and controller settings.

![screen](/NinaAndJess_XRBlog/images/rollabalVRscreen.png)

We also added a user interface displaying the number of collected coins and a victory message. This required linking UI text elements to variables tracking the player’s progress which had already been set up nicely from the last project. We just needed to set the variables.

Next, we implemented interaction with the Roll-a-Ball asset. We created scripts and added colliders so that pressing the trigger on either controller would interact with the game. We configured object layers to ensure that the selection colliders and the game colliders did not interfere with each other. We also made the entire game board grabbable. Because the ball already had collision physics with the board, tilting the board allowed the player to move the ball and even cause it to fall off if tilted too far.
Finally, we built and ran the completed application on the headset.

<video controls width="100%">
  <source src="/NinaAndJess_XRBlog/images/rollaballvr.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
