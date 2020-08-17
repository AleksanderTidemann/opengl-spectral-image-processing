# Exploring spectral mean images in Max/MSP/Jitter using OpenGL

<figure alignt="center">
   <img src="figure.gif" alt="figure"
   title="figure" width="640" />
   <figcaption></figcaption>
</figure>

[In a recent blogpost](https://aleksandertidemann.github.io/general/2020/08/04/exploring-spectral-mean-images.html), I conducted a small experiment to investigate whether an OpenGL system that generates real-time spectral mean images (or motiongrams) in Max/MSP/Jitter should do vector mean calculations on the CPU or the GPU. 

In short, I discovered that if you want a stable and highly controllable system that can accommodate various resolutions you should opt for doing a readback method that migrates the textures from the GPU to the CPU (specifically with [jit.gl.asyncread] and [xray.jit.mean]) before doing the mean calculations. This method is relatively [well documented by Cyling74 on their website](https://cycling74.com/tutorials/best-practices-in-jitter-part-1). On the other hand, if you're only going to process relatively low resolution images and want to utilize most of your CPU power elsewhere, you should avoid the readback method and rather use a for-loop inside a [jit.gl.pix] object to do the mean calculations.

In either case, you should always seek to downsample the image resolution beforehand. In light of this, I also provide an algorithmic approach to downsamplig your video content in the source code.  Both methods, labled "cpu-version" and the "gpu-version", are avaliable in the source folder.


## Dependencies
* XRAY external package

Thanks to [Federico Foderero](https://www.federicofoderaro.com/) for aiding me with some GenExpr programming syntax. 
