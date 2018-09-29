+++
date = "2018-05-27"
comments = true
draft = false
image = "/content/images/2018/may/engine-pbr/pbr.png"
slug = "custom-engine-pbr"
tags = ["custom-engine", "pbr", "opengl", "c++", "atmospheric-scattering"]
title = "Custom Engine: Physically Based Rendering"
description = "The physically based approach used for my custom rendering engine."

+++
<br>
### Index

- [Background](#background)
- [Physically Based Rendering](#physically-based-rendering)
	- [Introduction](#introduction)
	- [Physically Based Shading](#physically-based-shading)
	- [Image Based Lighting](#image-based-lighting)
	- [Merging](#merging)
- [Atmospheric Scattering](#atmospheric-scattering)
	- [Rayleigh Scattering](#rayleigh-scattering)
	- [Mie Scattering](#mie-scattering)
	- [Phase Functions](#phase-functions)
- [References](#references)

## Background

<p align="justify">
<b>Physically Based Rendering</b> is not a technique, but a collection of graphics techniques aiming to achieve results as close as possible to the <b>physical world</b>. This means that these techniques are highly based on real world physics light behaviour formulas. However, in order for these techiniques to be plausible to be rendered in real-time, some approximations need to be made (that is where the "based" in PBR comes from!).
</p>

<p align="justify">
In this post I will talk about the PBR techniques I implemented in my <a href="/render-engine">Custom Engine</a> (<b>physically based shading</b>, <b>image based lighting</b>, and <b>atmospheric scattering</b>) and what I learned while doing it. Lets go!
</p>

## Physically Based Rendering

#### Introduction

<p align="justify">
My implementation is highly based on <a href="https://learnopengl.com/PBR/Lighting" target="_blank">this tutorial</a>. Its basis are the following:
</p>


- <p align="justify"> <b>Be based on the microfacet surface model</b>: this theory describes how at a microscopic level, all surfaces have a certain degree of roughness which will scatter light rays in a more or less chaotic way, depending on this roughness degree.
</p>


<img src="/content/images/2018/may/engine-pbr/microfacets.png"/>

- <p align="justify"> <b>Be energy conserving</b>: This means that light leaving a surface, can never be brighter than the light that fell upon it; so the sum of the diffuse and reflected light cannot be bigger than the received light. As you can see in the image, as the surface gets smoother, the light reflected takes over the diffuse color of the sphere.
</p>

<img src="/content/images/2018/may/engine-pbr/energy-conservation.jpg" width ="100%"/>

- <p align="justify"> <b>Use a physically based BRDF</b>: The bidirectional reflectance distribution function used in this case is the Cook-Torrance BRDF. It is a function that models light behaviour in two different ways, making a difference between diffuse and specular reflection. This defines the way that light is reflected on the different surface models, and how the viewer sees the object.

<img src="/content/images/2018/may/engine-pbr/brdf.png" />

In the end, we get the Cook-Torrance <b>reflectance equation</b>, a more specialized version of the <a href="https://en.wikipedia.org/wiki/Rendering_equation" target="_blank">rendering equation</a>. 

<img src="/content/images/2018/may/engine-pbr/reflectance.png"/>
</p>

#### Physically Based Shading

<p align="justify">
I will not go into detail on how the reflectance function is translated into code, as the author of <a href="https://learnopengl.com/PBR/Lighting" target="_blank">the post</a> does a great job at explaining this. Once this functions are in the shader, computation for directional, point and spot lights is done in the shader, with the addition of the different light properties such as intensity/attenuation, ambient factor, color, cone angle in case of spot lights, and calculate the resulting light output keeping in mind the energy conservation rule.
</p>

```
refractedLight = 1.0 - reflectedLight
```
<p align="justify">
Now the lighting just needs the shadows to be applied to it, if any. Doing this is as simple as getting the resulting factor of shadow calculation and multiplying it by the output light.
</p>

<p align="justify">
This process is repeated for each light object, and summed to the final output value (as light is additive).
</p>

#### Image Based Lighting

<p align="justify">
For the IBL part, three preprocess passes are performed at the beggining of the application, in order to achieve the textures needed for the environment lighting of the PBR materials:
</p>

- <p align="justify"> <b>Diffuse Irradiance</b>: This process maps to a cube a blurred version of the environment cubemap, by convoluting each sample direction of the cubemap, and accumulating all other sample directions over a hemisphere, representing the sum of all indirect diffuse light of the scene hitting some surface with a certain normal direction. This texture result is known as irradiance map.

<img src="/content/images/2018/may/engine-pbr/irradiance.png"/>
</p>

- <p align="justify"> <b>Pre-filtered environment map</b>: This process is similar to the diffuse irradiance, but taking in roughness into account. Multiple level-of-detail cubemaps are convoluted, with more scattered sample vectors at each level (creating a blurrier result).

<img src="/content/images/2018/may/engine-pbr/prefilter.png"/>
</p>

- <p align="justify"> <b>BRDF</b>: The final bit that needs to be done is calculating the BRDF and mapping it to a lookup texture. Red represents a scale value, and green represents a bias value to the surface's Fresnel<sup>1</sup>, while the horizontal and vertical texture coordinates represent the BRDF's input <i>n ⋅ ω<sub>i</sub></i> value and the input roughness value, respectively.

<img src="/content/images/2018/may/engine-pbr/brdf_lut.png"/>
</p>

>>
Fresnel refers to the reflectivity occuring at different angles. Light landing on a surface at a grazing angle will be much more likely to reflect than that which hits a surface dead-on.
>>
<img src="/content/images/2018/may/engine-pbr/fresnel.png", width="90%"/>
\

#### Merging

<p align="justify">
In order to merge all this information into the final output color value, we need to calculate each part's contribution to it and add them together. The ambient factor is calculated as follows:
</p>

```
vec3 ambient = (kD * diffuse + specular) * ao_factor;
```

<p align="justify">
Being <i>kD</i> the refraction ratio, <i>diffuse</i> the irradiance multiplied by the albedo texture at that pixel, <i>specular</i> the prefiltered map value multiplied by the BRDF-LUT value, all based on roughness, and <i>ao_factor</i> the ambient occlusion value of the object at that pixel.
</p>

<p align="justify">
All that is left to do is to apply the high dynamic range (HDR) tonemapping, and gamma correction to the final output.

<img src="/content/images/2018/may/engine-pbr/tex_spheres.png" width="120%"/>
</p>


## Atmospheric Scattering

<p align="justify">
Even though this may seem like a completely unrelated topic, it really isn't. This technique <b>simulates the color of the sky based on physically based light scattering equations</b>. In order for this technique to be light-weight in performance, some simplification has to be done. In this case, the implementation assumes a single ray pointed to the viewers eye to simulate the light. 
</p>

<img src="/content/images/2018/may/engine-pbr/atmospheric_scattering_small.png" width="120%"/>

###### Single Scattering

<p align="justify">
This form of ray tracing is called <b>Single Scattering</b>. It means that a single ray of light can be deflected many times, so that light can travel very complex paths when colliding with molecules before reaching the camera. There are two ways in which this molecules can affect our vision:
</p>

- <p align="justify"><b>Out-Scattering</b>: happens when light is travelling towards the camera, and gets deflected by a collision with a particle. This is heavily affected by the distance that light has to travel. Distance makes the light to become progressively dimmer.
</p>

<img src="/content/images/2018/may/engine-pbr/out_scattering.png"/>

- <p align="justify"><b>In-Scattering</b>: happens when light is travelling in a direction, and gets deflected by a collision with a particle, which redirects it towards the camera. This allows us to see light sources that are not in the cameras direct light of sight, which causes halos around light sources.
</p>

<img src="/content/images/2018/may/engine-pbr/in_scattering.png"/>

<br>
<p align="justify">
Two of the most common forms of scattering in the atmosphere are <b><i>Rayleigh scattering</i></b> and <b><i>Mie scattering</i></b>. 
</p>

#### Rayleigh Scattering

<p align="justify">
Rayleigh scattering is the reason why we see the sky blue from the surface of the earth; it is caused by rays colliding with small particules in the air, which causes shorter light wavelengths to collide more frequently with them, scattering blue and violet<sup>2</sup> light along the sky, which bounces everywhere and makes the sky appear blue; however at sunset, the light has to travel through a lot more space so by the time it reaches our eye, all the blue and violet light is scattered away, leaving us only with the reddish light, making the sky appear orange and red.

<img src="/content/images/2018/may/engine-pbr/rayleigh.png" width="100%"/>
</p>


>> <p align="justify">
<b>2: Why is the sky blue and not violet?</b> TL;DR, even though violet light wavelength is shorter than blue, the Sun sends many less violet rays than blue rays, so the sky appears tinted in blue! </p>
>>
<p align="justify">Also, apart from this, the human eye has three types of cones to identify light color (red, green and blue). Blue cones, are most sensitive at blue wavelengths, but they drop sensitivity dramatically at violet wavelengths.
</p>

#### Mie Scattering

<p align="justify">
Mie scattering on the other side tends to scatter all wavelengths of light equally, as it refers to the collision with bigger particles (such as pollution and dust in the sky). It makes the sky look greyish and causes the sun to have a large white halo around it.

<img src="/content/images/2018/may/engine-pbr/mie_engine.png"/>
</p>

#### Phase functions

<p align="justify">
The phase function describes how much light is scattered towards the diraction of the acamara based on the angle and a constant <i>g</i> that affects the symmetry of the scattering. This is one adaptation of the full function:
</p>

<img src="/content/images/2018/may/engine-pbr/phase.jpg", width="70%"/>

<p align="justify">
However, for the sake of making this more lightweight, a huge level of simplification is applied to the function. The resulting equations used in the implementation are the following (for rayleigh and mie respectively):
</p>

<img src="/content/images/2018/may/engine-pbr/phases.png", width="90%"/>

<p align="justify">
Finally, the result of this functions is computed per pixel and drawn onto a cubemap. In the engine you can modify some parameters to describe different colors in the sky. You can see me playing with some values in the demo video (second 1:25):

<iframe width="560" height="315" src="https://www.youtube.com/embed/J9CExYF8yrU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## References

- <a href="https://learnopengl.com/PBR/Theory" target="_blank">LearnOpenGL PBR Theory</a>
- <a href="https://www.marmoset.co/posts/basic-theory-of-physically-based-rendering/" target="_blank">Marmoset PBR Guide</a>
- <a href="https://www.alanzucconi.com/2017/10/10/atmospheric-scattering-1/" target="_blank">Alan Zucconi Atmospheric Scattering</a>
- <a href="https://developer.nvidia.com/gpugems/GPUGems2/gpugems2_chapter16.html" target="_blank">GPU Gems: Atmospheric Scattering</a>