+++
comments = false
date = "2006-08-30T03:45:00+02:00"
draft = false
image = "images/cover-render-engine.png"
layout = "cover"
title = "Custom OpenGL C++ Engine"
description = "Rendering engine for HND final year's graphics programming subject."
type = "page"

+++

<iframe width="560" height="315" src="https://www.youtube.com/embed/J9CExYF8yrU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

### The Engine

<p align="justify">
This is an <b>OpenGL</b> and <b>C++</b> rendering engine I made in my final HND year at <a href="https://www.esat.es/" target="_blank">ESAT Valencia</a> for the graphics programming subject. Its main features are the following:
</p>

- Multithreaded agnostical graphics API
- Component oriented engine
- Physically Based Rendering techniques:
	- Material pipeline (PBS, Metallic/Roughness workflow)
	- Image Based Lighting (Radiance and Irradiance environment mapping)
	- Atmospheric Scattering (Rayleigh and Mie Scattering)
- GLTF model loading
- Postprocessing Pipeline:
	- Screen Space Ambient Occlusion (SSAO)
	- Bloom
	- Light Scattering (God Rays)
	- Shadow Mapping
	- Fast Approximate Anti-Aliasing (FXAA)
	- Lens Distortion (with Grain, Vignette, Color Aberration)
	- Tonemapping and multiple one-pass filters
- Procedural generation of infinite voxel worlds
- UI integration (ImGui)
- Sound integration (OpenAL)
- Physics integration (Bullet Physics)

---
### Related blog posts

>### [Custom Engine: Physically Based Rendering][1]
>The physically based approach used for my custom rendering engine.
>	<br><small><b>Víctor Ávila</b></small>

[1]: /post/custom-engine-pbr/
\

>### [Custom Engine: Postprocessing][2]
>My custom engine's postprocessing.
>	<br><small><b>Víctor Ávila</b></small>

[2]: /post/custom-engine-postprocessing/
\

---
### Gallery

<img src="/content/images/2018/aug/upydk/upydk_1.png", width="100%"/>
<img src="/content/images/2018/aug/upydk/upydk_2.png", width="100%"/>
<img src="/content/images/2018/aug/upydk/upydk_3.png", width="100%"/>
<img src="/content/images/2018/aug/upydk/upydk_4.png", width="100%"/>
<img src="/content/images/2018/aug/upydk/upydk_5.png", width="100%"/>