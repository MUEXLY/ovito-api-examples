# ovito-api-examples

The OVITO python API is a bit unintuitive. But, once you figure it out, it is super powerful.

Below are some examples of some very pretty figures you can make without having to pay for OVITO pro.

## A sharp edge

If you run into this error when trying to render an image with OVITO inside of an HPC environment:

```
qt.qpa.xcb: could not connect to display localhost:24.0
qt.qpa.plugin: From 6.5.0, xcb-cursor0 or libxcb-cursor0 is needed to load the Qt xcb platform plugin.
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vkkhrdisplay, vnc, wayland-egl, wayland, xcb.

Aborted (core dumped)
```

there is a very easy fix that is quite difficult to find. Namely, setting the following environment variable:

```py
import os
os.environ["OVITO_GUI_MODE"] = "1"
```

and running using the [X virtual framebuffer](https://en.wikipedia.org/wiki/Xvfb):

```bash
xvfb-run python script.py
```

Once you know this, you have quite a powerful tool on your hands.