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



<style>

.item-wrapper {
	width:33%;
	float: left;
}

.item {
  	text-align: center;
  	margin:20px;
}

.desc {
	text-align: left!important;
}

.clear {
  clear: both;
}

</style>

<div id="top" style="width:100%"> <!-- Images -->
	<div class="item-wrapper"> <!-- Item -->
		<div class="item">
			<a href="#fuel-renegades">
				<img src="/content/images/2019/01-jan/portfolio-fr.png" alt="Fuel Renegades" style="width:100%">	
			</a>
			<h4>Fuel Renegades</h4>
			<small><b>Description:</b> <i>Published PC Racing Multiplayer Game (<a href="https://store.steampowered.com/app/878110/Fuel_Renegades/">Steam</a>) (<a href="https://youtu.be/N2RG6a8gLr0">Video</a>)</i></small><br>
			<small><b>Tech:</b> <i>UE4, C++</i></small><br>
		</div>
	</div>
	<div class="item-wrapper"> <!-- Item -->
		<div class="item">
			<a href="#pbr-engine">
				<img src="/content/images/2019/01-jan/portfolio-engine.png" alt="PBR Engine" style="width:100%">	
			</a>
			<h4>PBR Game Engine</h4>
			<small><b>Description:</b> <i>Component Based, Multithreaded... (<a href="https://youtu.be/J9CExYF8yrU">Video</a>)</i></small><br>
			<small><b>Tech:</b> <i>C++, OpenGL</i></small><br>
		</div>
	</div>
	<div class="item-wrapper"> <!-- Item -->
		<div class="item">
			<a href="#vxr">
				<img src="/content/images/2019/01-jan/portfolio-vxr.png" alt="vxr" style="width:100%">	
			</a>
			<h4>vxr Rendering Engine</h4>
			<small><b>Description:</b> <i>Open Source (<a href="https://github.com/avilapa/vxr">GitHub</a>) PBR Engine + Final Year Project</i></small><br>
			<small><b>Tech:</b> <i>C++, OpenGL</i></small><br>
		</div>
	</div>
	<div class="item-wrapper"> <!-- Item -->
		<div class="item">
			<a href="#vxt">
				<img src="/content/images/2019/01-jan/portfolio-vxt.png" alt="vxt" style="width:100%">	
			</a>
			<h4>vxt Raytracer</h4>
			<small><b>Description:</b> <i>Open Source (<a href="https://github.com/avilapa/vxt">GitHub</a>) Multithreaded Path Tracer based on Peter Shirely's books</i></small><br>
			<small><b>Tech:</b> <i>C++</i></small><br>
		</div>
	</div>
	<div class="item-wrapper"> <!-- Item -->
		<div class="item">
			<a href="#rasterizer">
				<img src="/content/images/2019/01-jan/portfolio-rasterizer.png" alt="Rasterizer" style="width:100%">	
			</a>
			<h4>CPU Rasterizer</h4>
			<small><b>Description:</b> <i>Small C++ CPU rasterizer of triangle based convex meshes in Raspberry Pi 3</i></small><br>
			<small><b>Tech:</b> <i>C++</i></small><br>
		</div>
	</div>
	<div class="item-wrapper"> <!-- Item -->
		<div class="item">
			<a>
				<img src="/content/images/2019/01-jan/portfolio-ps4.png" alt="Rasterizer" style="width:100%">	
			</a>
			<h4>WIP: Roguelike PS4 Game</h4>
			<small><b>Description:</b> <i>Upcoming PS4 untitled game (university project)</i></small><br>
			<small><b>Tech:</b> <i>UE4, C++</i></small><br>
		</div>
	</div>
</div>

<div class="clear">
<hr>
</div>


#### <a id="fuel-renegades" href="/fuel-renegades/" target="_blank">Fuel Renegades (Steam Published Game) (Oct 2017 - Jul 2018)</a>

<font size="2">
<p align="justify" style="line-height:1.4">
<b>Link:</b> https://store.steampowered.com/app/878110/Fuel_Renegades/

<b>Arcade racing multiplayer</b> (4 players split-screen, up to 8 players online) game with <b>polished mechanics and smooth game feel</b>, built in <b>Unreal Engine 4</b> and published on Steam. Contributions to the project are:

 - __Player Vehicle design and implementation__: full implementation of vehicle movement mechanics with special emphasis on its feeling and speed.
 - Proper use of UE4 substepping system to achieve solid gameplay performance and __<a href="/post/framerate-independent-physics-in-ue4/" target="_blank">framerate independent physics</a>__ across computers with a wide range of specs.
 - Implementation of several __postprocessing effects__.
 - Several __UI design__ including the Main Menu.
 - Making of the __<a href="https://www.youtube.com/watch?v=N2RG6a8gLr0&list=PLxMwOQRJc15dLQrO0z1oc9JuXMaoGPlXd" target="_blank">video trailers</a>__ for the game.

 The game received the following <b>awards</b>:

- Best Videogame (Second Place), Student Game Contest ‘18, AEV Valencia.
- Best Technology (First Place), Student Game Contest ‘18, AEV Valencia..


<iframe width="560" height="315" src="https://www.youtube.com/embed/N2RG6a8gLr0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

<a href="#top"><i>Back to top</i></a>
</p>
</font>

#### <a id="pbr-engine" href="/render-engine/" target="_blank">PBR Game Engine (Oct 2017 - Jul 2018)</a>

<font size="2">
<p align="justify" style="line-height:1.4">
<b>OpenGL and C++ game engine</b> I made in my final HND year at ESAT Valencia for the graphics programming subject. This project was also my <b>first attempt at making a 3D engine</b>. Its features are the following:

- <b>Multithreaded</b> agnostical graphics API.
- <b>Component oriented</b> engine.
- <b>Physically Based Rendering</b> techniques:
	- Material pipeline (PBS, Metallic/Roughness workflow).
	- Image Based Lighting (Radiance and Irradiance environment mapping).
	- Atmospheric Scattering (Rayleigh and Mie Scattering).
- GLTF model loading.
- <b>Postprocessing</b> Pipeline: SSAO, Bloom, Light Scattering (God Rays), Shadow Mapping, FXAA, Lens Distortion, Tonemapping and multiple one-pass filters.
- Procedural generation of infinite voxel worlds.
- UI integration (ImGui).
- Sound integration (OpenAL).
- Physics integration (Bullet Physics).

<iframe width="560" height="315" src="https://www.youtube.com/embed/J9CExYF8yrU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

<a href="#top"><i>Back to top</i></a>
</p>
</font>


#### <a id="vxr" href="/vxr-engine/" target="_blank">vxr Engine (Open Source) (Jul 2018 - Ongoing)</a>

<font size="2">
<p align="justify" style="line-height:1.4">
<b>Link:</b> https://github.com/avilapa/vxr

Project that emerged from the desire to build a <b>general purpose rendering tool</b> that I could use to implement anything I was curious about or wanted to learn about.
As it stands now, it is a <b>multithreaded, PBR, 3D engine written in C++</b> and oriented to support different rendering backends. It is currently being worked on.

- Multithreaded agnostical graphics API
- Command Based Rendering, allowing to build the render commands in advance to be run in a separate thread
- _GameObjects_ with the following components currently implemented (each component is controlled and updated by a specific system):
  - Transform: Containing the object's transformation and position in the scene's hierarchy.
  - Mesh Filter: Reference to the mesh the object will be rendered with.
  - Renderer: Reference to the Material Instance the object will be rendered with.
    - Current Materials: Standard (Lit), Unlit, Wireframe, Skybox, Screen, Planet, ___Add your own!___
  - Light: Turns the object into a source of light.
  - Image Based Light: Light that captures the environment lighting into a diffuse irradiance map and a specular irradiance map for reflections.
  - Camera: Adds to an object all the functionality needed to render from its point of view with its unique parameters.
    - Camera Composer: Organizes all post-processing needed for any specific camera, and handles updates automatically.
      - Postprocessing Materials: One-Pass-Filters (Grayscale, Negative), ___Add your own!___
  - Custom Component: Similar to _Unity's MonoBehaviour_, allows the user to create custom reusable components with specific behaviours.
- Model loading (_.obj_)
- UI Editor

<img src="/content/images/2019/01-jan/vxr-teapot.png", width="100%"/>

<a href="#top"><i>Back to top</i></a>
</p>
</font>


#### <a id="vxt" href="/vxt-raytracer/" target="_blank">vxt Raytracer (Open Source) (Nov 2018)</a>

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

<a href="#top"><i>Back to top</i></a>
</p>
</font>

#### <div id="rasterizer"> CPU Rasterizer in Raspberry Pi 3 (May 2018 - June 2018)</div>

<font size="2">
<p align="justify" style="line-height:1.4">

Project for the <b>low level and optimization</b> subject in my final HND year. It consisted in implementing a graphics algorithm and applying as many optimization techniques as possible. 

- <b>CPU rasterization of triangle based convex meshes</b>.

<img src="/content/images/2018/oct/portfolio/cpu_rasterizer.png", width="100%"/>

<a href="#top"><i>Back to top</i></a>
</p>
</font>

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
