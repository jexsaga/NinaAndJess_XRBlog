+++
date = '2026-02-06T20:58:55+01:00'
draft = true
title = 'Locomotion Implementation'
+++


\
**1 LOCOMOTION IDEA**

Our first idea was to create a locomotion technique that is controlled with the position of your arms : 
With the two arms in front of you at the same height, you go forward. If the right hand is higher, you go left and vice versa. If your two arms are behind you, you go backward and if your two arms are in a rest position then you don't move.

![First Design](/NinaAndJess_XRBlog/images/armsVRsketch.jpeg)

When we were thinking about how we could actually implement it, we changed our idea slightly to better fit the project: now we actually use the controller’s triggers for the forward/backward movement. To go left and right we maintained the original idea of raising one arm higher, but we added the idea that the higher your arm is, the faster you rotate. We also added a jump and a boost for extra fun. 
So now, you can move using the index triggers, and jump with the inside buttons clicked at the same time. For the boost, the user just needs to put their two arms up and then they speed straight forward.

![Slides](/NinaAndJess_XRBlog/images/second_plan.png)


\
**2 FORWARD AND BACKWARD MOVEMENT**

<div style="display: flex; align-items: center; gap: 1rem;">
  <video controls width="50%">
    <source src="/NinaAndJess_XRBlog/images/beginning_source_code.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <p>The starting code provided with original locomotion technique.</p>
</div>

Firstly, we took the time to understand the code that was provided for us. Then, when we thought we understood, we quickly adjusted the code to prevent movement in the y direction. This was a temporary fix to the fact that our location technique does not defy gravity and a simple way for us to ensure we comprehended the code.

Next we handled more movement making the user able to go backward. We changed the method of movement to just be caused by pulling the controller triggers and allowed the user to go forward and backwards with constant acceleration. We did this by creating a value that increased while the player continued to hold the trigger up to a max value and then moved the player based on that value. This successfully simulated getting the player up to speed. We did this for both forward and backward directions and tweaked all the values in order to get the best result.

<div style="display: flex; align-items: center; gap: 1rem;">
  <p>This is the controller movement implimented without the constraint on y.</p>
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/forward_backward_not_fixed_y_but_controller_movement.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
  <video controls width="50%">
    <source src="/NinaAndJess_XRBlog/images/forward_backward_fixed_y.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <p>Here, you cannot "fly" even when the user looks upwards.</p>
</div>
    
We wanted to make it more complex by separating the positive and negative directions for acceleration so that it would feel more natural, but that idea did not inevitably add to the project so we went with the simpler approach.


\
**3 TURNING**

At this stage the user was able to move forward and backward with the triggers, but the forward direction was wherever the user looked. However, we wanted the rotation to be controlled by the arms. Furthermore, this initial implementation caused much motion sickness because as the player moved their head and pulled the right trigger they moved quickly in whatever direction they were looking, so it was hard for the player to get their bearings.

This was solved when we separated that rotation control from the camera rig. However, this created a problem with our forward and backward movement because now we only moved forward from wherever the player’s initial forward direction was and since rotation was not implemented, once the player turned their body to face the starting line they went backwards, previously their initial forward direction.

We already knew that in order to create the turning movement we wanted to have an initial y position to detect changes in the arm height. So, we created an auxiliary function to set the initial position of the player. We fixed our previous problem by allowing the user to orient themselves where they would like to go, aka towards the starting line, and then pull the triggers and inside buttons to initialize the set up. 

<video controls width="100%">
  <source src="/NinaAndJess_XRBlog/images/foward_backward.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

In doing this we were then ready to implement the turning movement with the arms such that if the user raised the right hand higher than the threshold, starting position y, they would turn left and if they raised the left hand higher than the threshold they would turn right. If both hands or neither were above the threshold they did not turn. All of this was possible by calculating the amplitude i.e. the distance between your current arms position and the initialized position. The amplitude directly affected the speed of rotation so that the user could make wide or tight turns at will. At this stage, everything was working but the speed variables needed to be slightly adjusted for the least amount of motion sickness.

<div style="display: flex; align-items: center; gap: 1rem;">
    <p>First problem: figure out how to turn. So, we made a 180 degree turn just to see. </p>
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/180_rotation_fast.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/endless_spinnningggg.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <p>Second, slow it down to make sure it is turning. </p>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
    <p>Next, implement rotation with hands.</p>
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/show_orientation_rotation_moving.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/show_orieving.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <p>Finally, adjust parameters to make the best movement.</p>
</div>


\
**4 BOOST**

Furthermore, this prepared us to implement the boost where if both hands were above a slightly higher threshold the player’s speed jumped up and they boosted forward.

<div style="display: flex; align-items: center; gap: 1rem;">
    <p style="width: 50%">Initial attempt.</p>
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/boooooost.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/boost_bien_show.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <p style="width: 50%">Faster!!</p>
</div>

\
**5 JUMP**

We now wanted to implement Jump. As a reminder, our idea for the jump was to make the user able to jump when he clicked on both inside buttons. Our first attempt was to use conditional statements and hardcoding the y position of the player. There were a lot of bugs and we foresaw many issues with this in handling the hill, so we decided to change directions.

<div style="display: flex; align-items: center; gap: 1rem;">
    <p style="width: 50%">First attempt with adjusting player y position directly.</p>
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/jump_inifiniiiii_et_bugs.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/jump_on_initialization_bug.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <p style="width: 50%">After getting a good jump. We needed to change initialization buttons to prevent jumping everytime.</p>
</div>



\
**6 GROUND COLLISION**

Undoing our temporary hard-coding of the y direction to prevent flying, we used Unity properties to create collision between the player and the ground as well as adding gravity to the player. This was an exceptionally difficult task because after checking all of the expected values in the rigid body, capsule colliders and mesh colliders we were still unable to fix the issue. Certain combinations of each parameter seemed to work better than others, but nothing worked entirely. Finally, we found that the terrain and interactables had not been placed into the correct layer. So, in changing this our player now moved along the ground and over the hill.

<div style="display: flex; align-items: center; gap: 1rem;">
    <p style="width: 50%">After correcting rigid body attributes interactibles caused collision.</p>
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/cant_go_through_start.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/weird_collision_affects.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <p style="width: 50%">Certain parameter selections cause random bugs like this.</p>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
    <p style="width: 50%">Adjusting capsule collider caused us to tip over.</p>
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/fallen_over.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="display: flex; align-items: center; gap: 1rem;">
    <video controls width="50%">
        <source src="/NinaAndJess_XRBlog/images/go_over_hill.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <p style="width: 50%">The correct implimentation resulted in this.</p>
</div>


Lastly, after implementing this we were able to use the rigid body to then create an upward impulse causing the player to jump.

\
**7 ALL TOGETHER**

Our final product:

<video controls width="100%">
    <source src="/NinaAndJess_XRBlog/images/demo.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>


(This video is not the best run. It is to demonstrate the controls.)
