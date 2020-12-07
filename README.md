# Real-time spectral mean images in Max/MSP/Jitter using OpenGL

[In a recent blogpost](https://aleksandertidemann.github.io/general/2020/08/04/exploring-spectral-mean-images.html), I conducted a small experiment to investigate whether an OpenGL system that generates real-time spectral mean images in Max/MSP/Jitter should do its vector mean calculations on the CPU or the GPU. 

In short, If you want a stable and highly controllable system that can accommodate various resolutions you should opt for doing a readback method that migrates the textures from the GPU to the CPU (specifically with ```[jit.gl.asyncread]``` and ```[xray.jit.mean]```). This method is relatively well documented by Cyling74 [on their website](https://cycling74.com/tutorials/best-practices-in-jitter-part-1). If you're only processing relatively low resolution images(!) and want to utilize most of your CPU power elsewhere, you should opt to keep the entire processes on the GPU.

Both versions as are included.

<p align="left">
 <img src="figure.gif" width=640>
</p>

## Dependencies
XRAY external package

Thanks to [Federico Foderero](https://www.federicofoderaro.com/) for aiding me with some GenExpr programming syntax. 
