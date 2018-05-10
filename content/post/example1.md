+++
date = "2014-07-11T10:54:24+02:00"
draft = true
image = "/content/images/2018/may/xativa.png"
slug = "framerate-independent-physics-in-ue4"
tags = ["fuel-renegades", "framerate", "independent", "physics", "ue4", "substepping"]
title = "Framerate independent physics in UE4"
description = "Achieving physics framerate independence in UE4 and how to correctly use substepping."

+++
<br>

<p align="justify">
If you are building a physics based game/application and you have plans of it running in a wide range of computers, <b>you need to fix your physics timestep</b>.
</p>

### Index

- [Understanding the problem](#understanding-the-problem)
- [Solving the problem](#solving-the-problem)
	- [Configuring substepping](#configuring-substepping)
	- [Setting up substepping in code](#setting-up-substepping-in-code)
	- [Handling substep physics](#handling-substep-physics)


## Understanding the problem

<p align="justify">
Your game may be running fine at 120 fps in your computer, but lower-end computers out there waiting for your game to come out may not be able to even reach 60 fps. Having the physics tied up to the application delta time causes the following behaviour when you apply the same torque to an object at 120 and 30 fps.
</p>

<small ><i>Torque applied at 120 fps (note that the gif is clamped at 33 fps):</i></small>
<img src="/content/images/2018/may/substepping/high_fps_right.gif" width="80%"/>

<small><i>Torque applied at 30 fps (literally unplayable!):</i></small>
<img src="/content/images/2018/may/substepping/low_fps_wrong.gif"  width="80%"/>

<p align="justify">
Fixed physics time steps allow the application physics simulation system to run always at the same speed independently from the current framerate. Unreal Engine 4 allows you to fix your physics timestep with <b>Substepping</b>. Using this technique, the previous example will now behave like this:
</p>

<small><i>Torque applied at 10 fps (substepping enabled):</i></small>
<img src="/content/images/2018/may/substepping/low_fps_right.gif"  width="80%"/>

>>
<small><i> Tip: you can use commands <b>~ Stat FPS</b> to display the current fps counter, and <b>~ t.MaxFPS 30</b> to lock the application fps to 30 for this test (remember using <b>t.MaxFPS -1</b> to reset).</i></small>

<p align="justify">
A fixed physics timestep will allow every user of your application to use it at the same speed regardless of their framerate.
</p>


## Solving the problem

<p align="justify">
Substepping is a technique that allows the engine to <b>subdivide the <i>Tick()</i> into multiple sub-ticks in order to reproduce more physics ticks to reach the desired physics delta time</b>. Good news is UE4 does this internally, and it is completely hidden to the user. However, if you are going to implement this, you will have to work a little differently with physics.
</p>

#### Configuring substepping


<p align="justify">
You can enable substepping by ticking <i>Project Settings > Physics > Framerate > Substepping</i>. There are a couple <b>configuration settings</b> to take into account here.
</p>

<img src="/content/images/2018/may/substepping/substepping.png" width="100%"/>

###### Max Substep Delta Time

This delta defines the time above which the physics engine will need to perform substeps. It will perform as much substeps as needed to reach 1 / max-substep-delta-time (1 / 0.008333 = 120fps in this case). You 

For example, in [Fuel Renegades](/fuel-renegades), we needed the physics to run at 120 fps (0.008333) in order for them to be as deterministic as possible

###### Max Substeps

a

#### Setting up substepping in code

a


#### Handling substep physics

a

### Going further

### Problems

cpu overload, means physics overload (max substep!)


### Why doesn't UE4 use a fixed timestep?

<p align="justify">
Unlike Unity3D (using a fixed timestep) Unreal Engine 4 is using a semi-fixed timestep. As the Epic Games developer Ori Cohen says:
</p>

>>
We actually had a debate about these two techniques and eventually decided on semi-fixed, and here's why:
>>
If you use Free the physics you have to use a timebank. If you want to tick physics at 60fps and you have a frame that took a little bit more than 1/60 you will need to have some left over time. Then you will tick the physics engine with the perfect 1/60 delta time, leaving the remainder for the next frame. The problem is that the rest of the engine still uses the original delta time. This means that things like blueprint will be given a delta time of 1/60 + a bit. 
>>
You can imagine a case where a user would want to use delta time in blueprint to determine the location of an object that's moving at some constant speed by saying "new position = old position + speed * delta time"
In such a case the user will expect the object to move speed * delta time. However, since delta time is longer the the time we tick a single physics frame, we would need to either brake the movement into two physics ticks to maintain the right speed, or we would have to place the object in the new expected position at the end of the frame, but increase speed. Either way the result isn't what the user would expect.
>>
Getting the rest of the engine to use this new delta time would affect many systems, and so we ultimately decided to go with semi fixed. 
\

##### Special Thanks