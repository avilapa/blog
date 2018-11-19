+++
comments = false
date = "2006-08-30T03:45:00+02:00"
draft = false
image = "/content/images/2018/nov/vxt/vxt_banner.jpg/"
layout = "cover"
title = "vxt Raytracer (Open Source)"
description = "Multithreaded CPU based path tracer built from scratch in C++."
type = "page"

+++

<img src="/content/images/2018/nov/vxt/raytracing_collage.jpg/", width="100%"/>

### The Raytracer

<p align="justify">
<b>vxt</b> is a CPU based multithreaded path tracing renderer written in C++, based on the book Ray Tracing the Next Week by Peter Shirley. The purpose of this project is purely academic as this is my first contact with path tracing techniques! So far so fun :^) 
</p>

### Features

- Multithreaded Tiled Rendering in CPU.
- Creation of Image Previews in the process.
- Objects: Sphere, Box, Axis Aligned Plane, Volume, AABB (all capable of being Translated and Rotated).
- Bounding Volume Hierarchy Acceleration Structure.
- Materials: Lambertian, Metal, Glass, Isotropic (Fog/Smoke), Diffuse Light.
- Textures (used in all materials): Image Based, Noise, Custom.
- Realistic Camera: Depth of Field, Motion Blur.

<b>Github page: https://github.com/avilapa/vxt</b>

---
### Gallery

<img src="/content/images/2018/nov/vxt/output_final_10000spp.jpg", width="100%"/>
<img src="/content/images/2018/nov/vxt/output_cornell_smoke_scene_500spp.jpg", width="100%"/>
<img src="/content/images/2018/nov/vxt/output_100spp.jpg", width="100%"/>
<img src="/content/images/2018/nov/vxt/output_noises_200spp.jpg", width="100%"/>