void draw_single_ray(SDL_Surface *surface, ray_t ray, circle_t base_source)
{
    double dx = ray.x - base_source.x;
    double dy = ray.y - base_source.y;
    double dist = sqrt(dx * dx + dy * dy);

    double brightness = 1.0 - (dist / 500.0); // intensity
    if (brightness < 0.1)
        brightness = 0.1;
    if (brightness > 1.0)
        brightness = 1.0;

    uint8_t r = (uint8_t)(255 * brightness);
    uint8_t g = (uint8_t)(236 * brightness);
    uint8_t b = (uint8_t)(153 * brightness);

    uint32_t ray_color = (r << 16) | (g << 8) | b;

    //  [Byte 3:red] [Byte 2:green] [Byte 1:blue] [Byte 0:Unused]
    //  16 - 23      8 - 15           0 - 7

    SDL_Rect ray_point =
        (SDL_Rect){ray.x, ray.y, RAY_THICKNESS, RAY_THICKNESS};
    SDL_FillRect(surface, &ray_point, ray_color);
}
