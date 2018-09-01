+++
date = "2018-09-01"
draft = false
image = "/content/images/2018/sep/vxr/new-beginnings.png"
slug = "vxr-new-beginnings"
tags = ["vxr"]
title = "VXR: New beginnings"
description = "First blog post of the development process of the VXR engine."

+++
<br>
### Index

- [New beginnings](#new-beginnings)
	- [Introduction](#introduction)
	- [Goals](#goals)
	- [The first weeks!](#the-first-weeks)
- [Up next](#up-next)
- [References](#references)

## New beginnings

### Introduction

<p align="justify">
VXR is a project that emerged from the desire to build a general purpose rendering tool that I could use to implement anything I was curious about or wanted to learn about. It was <i>quickly restated</i> and expanded as <b>the tool on which my Bachelor's degree personal project would take form</b> during this next year.
</p>

<p align="justify">
Also, as a personal exercise, I will try to keep this page updated with the development process of the engine.
</p>

### Goals

<p align="justify">
I'm still unsure about which subject I would like to explore in my personal project. I do have however a sense of more or less what is it going to be (still needs aproval from whoever will be tutoring me this project!). Here are some topics I would enjoy trying out for VXR:
</p>

- Multithreaded agnostical graphics API
- Multiple Graphic Backends (such as OpenGL, DirectX, Vulkan...)
- Physically Based Rendering oriented
- Exploring Raytracing techniques:
	- GPU Path Tracing
	- Real Time Raytracing
	- Hybrid Pipeline / Easily interchangeable Raster-Raytrace drawing
- More advanced Material Editing Visualization tools

<p align="justify">
Keep in mind this is a little chaotic, and the scope will be more defined as I choose a topic and have a clearer vision of what can be achieved and what is unrealistic.
</p>

### The first weeks!

<img src="/content/images/2018/sep/vxr/new_beginnings/hellotriangle.png", width="100%"/>

<p align="justify">
Two weeks have passed since I wrote the first line of code and its been so fun! I am really proud of the results I am achieving and how much I'm learning from just reimplementing things in different ways.
</p>

<p align="justify">
As I've developed a clear joy on graphics and engine programming for the moment I am building a <b>multi-purpose rendering engine</b>, applying all the great stuff I learned from the development of <a href="/render-engine" target="_blank"><i>UPyDK</i></a>, and avoiding pitfalls and problems found there. Also I have taken <i>great inspiration</i> from the recently released <a href="https://github.com/pplux/px/blob/master/README_px_render.md" target="_blank"><i>Single Header C++ Command Based backend renderer, <b>px_render.h</b></i></a>, which has a really similar mindset and structure to <i>UPyDK</i> (as the developer of <i>px_render.h</i> was actually my teacher!), but is implemented in a way more polished and functional way.
</p>

<p align="justify">
In order to safely try out some new organization in the engine I decided to start coding from known ground and began to make using OpenGL for the rendering (though it's been made really easy to add a new backend).
</p>
<p align="justify">
The main differences so far have been regarding the <b>render commands</b> and the treating of <b>uniform data</b>:
</p>

<p align="justify">
- <b>Render Commands</b>: The amount of render commands has been significantly lowered, as I realized I didn't need so many different commands when less could do the trick quicker and more intuitively for the user. This also reduced memory usage, and made it easier for me to organize the stuff. Multithreading remains the same for now (two syncrhonized threads for logic and render), but the newly added <i>RenderContext</i> structure helps make command data more independent and avoid future possible race conditions.
</p>

<p align="justify">
- <b>Uniform Data</b>: In UPyDK it was a bit uncomfortable to add custom uniforms to new materials. They were always stored in a <i>big vec4 matrix</i>, passed each frame on to each program, and then given a name to each of the <i>vec4 x y z w</i> components in order for the data to be more easily readable. Instead VXR makes use of the <i>OpenGL</i>'s <i><b>Uniform Buffer Objects</b></i>. These are not only easier to use but also more efficient, as the user can define multiple structures and update them only once to be used in multiple <i>programs</i> at a time. With a really simple API, these buffers are declared <i>Static</i> or <i>Dynamic/Stream</i> depending on if they need to be updated each frame or not.
</p>

<img src="/content/images/2018/sep/vxr/new_beginnings/cube.gif", width="100%"/>

<p align="justify">
As for new things I finally decided on implementing instancing, as with the practical example of <a href="https://github.com/pplux/px/blob/master/README_px_render.md" target="_blank"><i><b>px_render.h</b></i></a> it could be considered a crime not to...
</p>
<p align="justify">
Quickly after that I added textures to the instancing scene, and thought that it could be nice to keep track of the development of VXR on my blog!
</p>
<img src="/content/images/2018/sep/vxr/new_beginnings/instancing.gif", width="100%"/>

>>
That's 45.000 cubes!

## Up next

In exactly three weeks I will be moving to the UK to start my last year of the Bachelor's Degree, so I'll be getting ready for that!

## References

- <a href="https://github.com/pplux/px/blob/master/README_px_render.md" target="_blank">px_render.h</a>
- <a href="https://www.khronos.org/opengl/wiki/Uniform_Buffer_Object" target="_blank">OpenGL Uniform Buffer Objects</a>