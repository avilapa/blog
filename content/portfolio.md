+++
comments = false
draft = false
noauthor = true
share = true
title = "Portfolio"
type = "page"
layout = "cover"
image = "/content/images/2018/aug/upydk/upydk_1.png"
+++
>> You can read a little bit <a href="/about/" target="_blank">about me</a> first!


#### <a href="/fuel-renegades/" target="_blank">Fuel Renegades (UE4 Steam Published Game)</a>

<font size="2">
<p align="justify" style="line-height:1.4">
<b>Link:</b> https://store.steampowered.com/app/878110/Fuel_Renegades/

<b>Arcade racing multiplayer</b> (4 players split-screen, up to 8 players online) game with <b>polished mechanics and smooth game feel</b>, built in <b>Unreal Engine 4</b> and published on Steam. My main contributions to the project are:

 - __Player Vehicle design and implementation__: full implementation of vehicle movement mechanics with special emphasis on its feeling and speed.
 - Proper use of UE4 substepping system to achieve solid gameplay performance and __<a href="/post/framerate-independent-physics-in-ue4/" target="_blank">framerate independent physics</a>__ across computers with a wide range of specs.
 - Implementation of several __postprocessing effects__.
 - Several __UI design__ including the Main Menu.
 - Making of the __<a href="https://www.youtube.com/watch?v=N2RG6a8gLr0&list=PLxMwOQRJc15dLQrO0z1oc9JuXMaoGPlXd" target="_blank">video trailers</a>__ for the game.

<iframe width="560" height="315" src="https://www.youtube.com/embed/N2RG6a8gLr0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

</p>
</font>
<hr>

#### <a href="/render-engine/" target="_blank">PBR Engine</a>

<font size="2">
<p align="justify" style="line-height:1.4">
<b>OpenGL and C++ rendering engine</b> I made in my final HND year at ESAT Valencia for the graphics programming subject. This project was also my <b>first attempt at making a 3D Engine</b>. Its features are the following:

- Multithreaded agnostical graphics API.
- Component oriented engine.
- Physically Based Rendering techniques:
	- Material pipeline (PBS, Metallic/Roughness workflow).
	- Image Based Lighting (Radiance and Irradiance environment mapping).
	- Atmospheric Scattering (Rayleigh and Mie Scattering).
- GLTF model loading.
- Postprocessing Pipeline: SSAO, Bloom, Light Scattering (God Rays), Shadow Mapping, FXAA, Lens Distortion, Tonemapping and multiple one-pass filters.
- Procedural generation of infinite voxel worlds.
- UI integration (ImGui).
- Sound integration (OpenAL).
- Physics integration (Bullet Physics).

<iframe width="560" height="315" src="https://www.youtube.com/embed/J9CExYF8yrU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
</p>
</font>
<hr>


#### <a href="/vxt-raytracer/" target="_blank">vxt Raytracer (Open Source)</a>

<font size="2">
<p align="justify" style="line-height:1.4">
<b>Link:</b> https://github.com/avilapa/vxt

First contact with ray tracing and offline rendering techniques in C++. Multithreaded CPU
based path tracer built from scratch.

- Multithreaded Tiled Rendering in CPU.
- Creation of Image Previews in the process.
- Objects: Sphere, Box, Axis Aligned Plane, Volume, AABB (all capable of being Translated and Rotated).
- Bounding Volume Hierarchy Acceleration Structure.
- Materials: Lambertian, Metal, Glass, Isotropic (Fog/Smoke), Diffuse Light.
- Textures (used in all materials): Image Based, Noise, Custom.
- Realistic Camera: Depth of Field, Motion Blur.

<img src="/content/images/2018/nov/vxt/raytracing_collage.jpg", width="100%"/>
</p>
</font>
<hr>

#### <a href="/vxr-engine/" target="_blank">vxr Engine (Open Source)</a>

<font size="2">
<p align="justify" style="line-height:1.4">
<b>Link:</b> https://github.com/avilapa/vxr

Project that emerged from the desire to build a <b>general purpose rendering tool</b> that I could use to implement anything I was curious about or wanted to learn about.
As it stands now, it is a <b>multithreaded 3D engine written in C++</b> and oriented to support different rendering backends. It is currently being worked on.

- Multithreaded agnostical graphics API.
- Command Based Rendering, allowing to build the render commands in advance to be run in a separate thread.
- GameObject - Component - System oriented engine.

<img src="/content/images/2018/oct/portfolio/vxr.png", width="100%"/>
</p>
</font>
<hr>

#### CPU Rasterizer in Raspberry Pi 3

<font size="2">
<p align="justify" style="line-height:1.4">

Project for the <b>low level and optimization</b> subject in my final HND year. It consisted in implementing a graphics algorithm and applying as many optimization techniques as possible. 

- <b>CPU rasterization of triangle based convex meshes</b>.

<img src="/content/images/2018/oct/portfolio/cpu_rasterizer.png", width="100%"/>
</p>
</font>
<hr>

<!--
#### Multi-Agent System and A* Pathfinding

<font size="2">
<p align="justify" style="line-height:1.4">

Project for the Artificial Intelligence subject in my final HND year. It consisted in implementing several agents each with its specific behaviour to simulate a prison. 

- <b>A* Pathfinding</b> agent used to communicate with the agents and provide them with requested paths.
- Prisoner, Soldier and Guard agents with using <b>FSM</b> for their movement and behaviour (mind - body). 
- Prison agent used to communicate with the agents.
- Multi-Agent messaging.
- <b>Fixed timestep</b>.

<img src="/content/images/2018/oct/portfolio/prison.png", width="100%"/>
</p>
</font>
<hr>

#### Procedural City (Graphics Framework)

<font size="2">
<p align="justify" style="line-height:1.4">

First contact with graphcis for the graphics programming subject in my second year. The project consisted on learning OpenGL by implementing Texture, Framebuffer, Material and Buffer objects in a C++ OpenGL framework, and testing them by building a procedural city.

- Exploration of procedural generation algorithms.
- <b>Screen Space Ambient Occlusion</b> postprocess.
- <b>Deferred Rendering</b>. 

<img src="/content/images/2018/oct/portfolio/city.png", width="100%"/>
</p>
</font>
<hr>

#### Star Castle

<font size="2">
<p align="justify" style="line-height:1.4">

Implementation of the classic arcade game Star Castle in a small university rendering framework done in the first year.

- No sprites used in gameplay, all vector and matrix rendering.
- Collision system.
- Progression system with unlockable levels and progressive difficulty.
- Login system and management on a separate application.
- High scores.

<img src="/content/images/2018/oct/portfolio/star_castle.png", width="100%"/>
</p>
</font>
<hr>

#### Game Jams

<font size="2">
<p align="justify" style="line-height:1.4">

I have participated in several Game Jams in Ludum Dare, and privately organized ones. In all of them I used <b>Unity 3D</b>. Most of them were group based.

<img src="/content/images/2018/oct/portfolio/game_jams.png", width="100%"/>
</p>
</font>
<hr>
-->
