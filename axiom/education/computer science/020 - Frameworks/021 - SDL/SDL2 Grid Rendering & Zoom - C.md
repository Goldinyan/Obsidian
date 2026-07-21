Date: 2026-01-11
Tags: {
#W
[[%C]]
[[%SDL]]
[[%GUI]]
}


# SDL2 Grid Rendering & Zoom - C


## Renderer
Der Renderer ist das GPU‑Zeichenmodul von SDL.  
Er verwaltet Farben, zeichnet Primitive und Texturen, löscht den Backbuffer und präsentiert den fertigen Frame.  
Fenster und Renderer sind getrennt: Das Fenster zeigt nur an, der Renderer zeichnet.

Ablauf pro Frame:
1. Zeichenfarbe setzen  
2. Backbuffer löschen  
3. Linien, Rechtecke, Texturen zeichnen  
4. Backbuffer mit Present anzeigen  

## Grid-Konzept
Das Grid wird in Bildschirmkoordinaten gezeichnet.  
Der Abstand zwischen den Linien wird durch den Zoomfaktor skaliert.  
Die Kamera verschiebt das Grid, ohne dass es springt.

Parameter:
```
zoom       // Skalierung
grid_size  // Weltabstand der Linien
cam_x      // Kameraoffset X
cam_y      // Kameraoffset Y
```

## Skalierung
```
scaled = grid_size * zoom
```
Beispiel: grid_size 50, zoom 2 → Abstand 100 Pixel.

## Offset
```
offset_x = fmodf(-cam_x * zoom, scaled)
offset_y = fmodf(-cam_y * zoom, scaled)
```
Der Startpunkt der Linien wird verschoben, damit das Grid stabil bleibt, wenn die Kamera bewegt wird.

## Vertikale Linien
```
for (float x = offset_x; x < screen_w; x += scaled)
    SDL_RenderDrawLine(r, x, 0, x, screen_h);
```
Start bei offset_x, danach alle scaled Pixel eine Linie.

## Horizontale Linien
```
for (float y = offset_y; y < screen_h; y += scaled)
    SDL_RenderDrawLine(r, 0, y, screen_w, y);
```
Start bei offset_y, danach alle scaled Pixel eine Linie.

## Render-Loop
```
SDL_SetRenderDrawColor(renderer, 20, 20, 20, 255);
SDL_RenderClear(renderer);

draw_grid(renderer, screen_w, screen_h,
          zoom, grid_size, cam_x, cam_y);

SDL_RenderPresent(renderer);
```

## Zoom-Steuerung
```
if (e.type == SDL_KEYDOWN) {
    if (e.key.keysym.sym == SDLK_EQUALS) zoom *= 1.1f;
    if (e.key.keysym.sym == SDLK_MINUS)  zoom /= 1.1f;
}
```
---------



# References