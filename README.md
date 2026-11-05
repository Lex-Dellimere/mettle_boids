# mettle_boids

Boids flocking on the GPU, written in [Mettle](https://github.com/The-Mettle-Project/Mettle) with [Glint](https://github.com/Lex-Dellimere/Glint) (OpenGL 4.6).

Every frame, compute shaders put the boids into a grid, sort them by cell, and steer each one by the boids in the 27 cells around it: separation, alignment, cohesion, a soft box and a predator to flee. One instanced draw call renders them. 131072 boids take about 0.4 ms a step on an RTX 4070.

## Build and run

Needs Glint checked out at `../mettle/glint` and a GPU with OpenGL 4.3 or newer.

```bash
mbuild run boids
mbuild run boids -- --boids 500000
mbuild run boids -- --headless out.ppm
```

On a laptop with an NVIDIA GPU behind the main one (PRIME):

```bash
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia GLINT_BACKEND=glx mbuild run boids
```

## Controls

Drag to orbit, scroll to zoom, R resets the camera, Space pauses, P toggles the predator, Escape quits.

The shaders in `shaders/` reload when you save them.

## License

Apache-2.0
