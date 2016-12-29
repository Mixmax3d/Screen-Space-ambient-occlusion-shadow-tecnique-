First of all : this implementation, is based on a simple deferred pipeline and it works quite well on the system on which has been developed. 

In order to operate, this implementation needs an hardware support for Opengl Frame Buffer Object (FBO) extensions.

The SSAO shader is a complex topic, after fifty attempts I came to this result : it's not perfect, it's not the best, 
and it's not as accurate as other I saw, but in final composition looks artistically good enough for its own purpose: 
increase the perception of scene's depth.

The shader works on a pre-pass that defines a visual rappresentation of the normals and depth of the scene in screen space.
The SSAO shader calculates per-pixel ambient occlusion using a Poisson distribution within a goniometric circumference 
taking samples (currently 32) along the directions of the normals of the scene's sample. 
If the occlusion's conditions is been respected, the shader accumulates an occlusion sample factor 
and it displays it on the screen. Luckily the result does not need bilateral blur passes.
