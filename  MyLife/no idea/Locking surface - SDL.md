---
id: Locking surface - SDL
aliases:
Topic: How to lock SDL Surfaces and why.
Related:
Tags:
  - w
Date:
Updated:
Source:
---
# Locking surface - SDL

  

#### What “locking the surface” actually means 

SDL surfaces sometimes store pixels in memory formats that the CPU cannot safely write to directly (because the GPU or OS might be using them).

So SDL requires this pattern:

1. Lock the surface → SDL gives you safe, direct access to the pixel buffer
2. Write pixels yourself → super fast
3. Unlock the surface → SDL can use the surface again

That’s it.

##### What is pitch and why do we need it?

Pitch = number of bytes in one row of pixels.

We need it for pointer arithmetic.

It is NOT equal to width because:

- SDL may pad rows for alignment
- Some formats store extra bytes
- Some surfaces have different memory layouts

So you cannot compute pixel positions using:

index = y * width + x   

Instead you must use:

index = y * pitch_in_pixels + x  

Since pitch is in bytes, and each pixel is 4 bytes (ARGB8888), we convert:

```c
int pitch = surface->pitch / 4;
```

Now pitch is “pixels per row”.

  

## Compact summary of the whole locking process

Here’s the entire concept in 6 lines:

1. SDL surfaces may not be directly writable.
2. SDL_LockSurface() gives you a pointer to raw pixel memory.
3. surface->pixels is the start of the pixel buffer.
4. surface->pitch tells you how many bytes each row occupies.
5. Convert pitch to pixels: pitch = pitch_bytes / 4.
6. Write pixels using: pixels[y * pitch + x] = color.

