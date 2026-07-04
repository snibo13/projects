---
title: "You Gotta Feel It"
date: 2026-07-03T22:52:38-07:00
draft: false
list: true
---

Manipulation is fundamentally the exchange of forces between the manipulator and manipulated to change the state. This "state" could be a variety of things: position, velocity, orientation and additional internal configurations (like opening a book or unscrewing a bottle).

In robotics the current belle of the ball for manipulation is the VLA (vision-language-action) policy: image and language conditioned model that generates joint trajectories. And these are popular for good reason, they've initiated a step function in manipulation performance and offer alternatives to previous brittle, manually engineered task policies.

For several of these manipulations moving from position a to position b is sufficient. For a pick and place task you move to roughly the correct location, move the gripper to be roughly closed, move to the target and release. Under the hood, VLA policies are effectively language prompted visual servoing. Using a prompt and images to determine the targets implicitly. This has proven to be effective for some tasks, but has struggled with highly dexterous tasks.

I think for dexterous tasks the inclusion of tactile sensing and force control will be necessary for highly successful policies.

Many tasks that can be accomplished fully blind. When we insert a key we aren't carefully aligning the key with the slot. We get close and run the last mm of manipulation with tactile feedback. Maybe it's just me, but some tasks are actually easier when I look away and focus on just feeling it. 

Visual servoing will only be as good as what it can see. Occlusion and loss of detail from dropping image resolution to 0.2 MP (for context the first phone with a camera in 1999 had 0.11 MP) will limit the usable information for small movements that dexterity requires. Not to mention the need to high frequency control loops to stabilize contacts or do any non quasi-static tasks.

For dynamic, dexterous tasks I would bet on high frequency policies that rely almost exclusively on tactile feedback. Images are useful for the macro-manipulations but micro-manipulations? You gotta feel it.