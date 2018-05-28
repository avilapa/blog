+++
comments = false
date = "2018-05-27"
draft = false
image = "/content/images/2018/may/engine-postprocessing/pp.png"
slug = "custom-engine-postprocessing"
tags = ["custom-engine", "postprocessing", "opengl", "c++", "ssao", "bloom", "fxaa", "lens-distortion"]
title = "Custom Engine: Postprocessing"
description = "The postprocessing pipeline and some of its postprocessing effects in my custom rendering engine."

+++
<br>
### Index

- [Postprocessing Pipeline](#postprocessing-pipeline)
- [Postprocessing Effects](#postprocessing-effects)
	- [SSAO](#ssao)
	- [Bloom](#bloom)
	- [God Rays](#god-rays)
- [References](#references)

## Postprocessing Pipeline

<p align="justify">
The goal of the pipeline was to make an API that is really easy to use for the users, and that requieres as little graphics knowledge as possible. The result, is as simple as the following:
</p>

```
ref_ptr<Composer> cam_composer = Engine::ref().scene()->camera()->composer();

cam_composer->set_shadow_mapping_enabled(true);
cam_composer->addPostprocessSSAO()->addPostprocessBloom()->addPostprocessFXAA();
```

This API makes some assumptions:

- <p align="justify">The user will not create new postprocessing effects, they will just be able to compose the scene and tweak each render passes parameters.</p>
- <p align="justify">Some postprocessing effects will just simply not be compatible together, but no one will stop the user from trying to set them up together, and you will just see one of the two in action.</p>
- <p align="justify">The results will not be the most incredible performance-wise, due to redundant calls and prepasses just to be able to treat each postprocess atomically and simplify the lecture.</p>

<p align="justify">
However, the composer class could of course be overriden to create a faster and more optimized composer that really makes use of its passes and reuses them, but this would need to be made by the developer.
</p>

<p align="justify">
In an ideal world (like the one in Unity3D or UE4), the composer would be smart enough to recognize the amount of postprocessing effects it has to perform, and understand when can it reuse a render pass. But this would have consumed time I rathered invert in other stuff!
</p>

<p align="justify">
But the user does have some degree of control when it comes to sort of composing their own passes. Each <i>addPass()</i> call receives two optional parameters, an input texture, and a pointer to an output texture. This way, the user could compose a complex pass like this example, composing god rays:
</p>

```
ref_ptr<Texture> blurred_tex;
blurred_tex.alloc();

cam_composer->addPassGaussianBlur(4, NULL, &blurred_tex);
cam_composer->addPassNegativeFilter(NULL, NULL);
cam_composer->addPassBlend(NULL, blurred_tex, NULL);
```

<p align="justify">
By passing NULL (or just nothing) to the input and output parameters, the composer identifies that the postprocess should use as input the output of the last performed render pass. When overriding the input parameter, the new texture is used as input. When passing a texture object to the output field, the user obtains the output of that render pass on that texture (as done in the <i>Gaussian Blur</i> pass). This can be later used to pass it as an input parameter for another pass. In this case, <i>Blend</i> pass receives two input textures, so by sending the previous output texture we have effectively performed a blend between two previous passes.

This example may seem kind of lame, but it has been core to being able to easily implement more complex postprocessing effects such as SSAO or God Rays.
</p>

## Postprocessing Effects

<p align="justify">
</p>

#### SSAO

<p align="justify">
</p>

#### Bloom

<p align="justify">
</p>

#### God Rays

<p align="justify">
</p>

## References

- <a href="http://john-chapman-graphics.blogspot.com.es/2013/01/ssao-tutorial.html" target="_blank">John Chapman SSAO</a>
- <a href="https://learnopengl.com/Advanced-Lighting/SSAO" target="_blank">LearnOpenGL SSAO</a>