Date: 2026-01-11
Tags: {
#W
[[%C]]
[[%SDL]]
[[%GUI]]
}


# Tracking Input SDL - C


```c
include "SDL2/SDL_keycode.h"

SDL_Event e;

// Init an event

while(running)
{
	while(SDL_PollEvent(&e))
	{
	// You need a pointer to 
	// the event
	
		if(e.type == SDL_MOUSEMOTION || e.type == SDL_MOUSEBUTTONDOWN){
			mouse_x = e.motion.x;
			// setting mouse position
			mouse_y = e.motion.y;
		}
		
		if (e.type == SDL_MOUSEBUTTONDOWN)
	    {
	        if (e.button.button == SDL_BUTTON_LEFT)
		    {
	          printf("left click at %d %d\n", e.button.x, e.button.y);
          
	        }
	        
	        if (e.button.button == SDL_BUTTON_RIGHT)
	        {
	          printf("right click at %d %d\n", e.button.x, e.button.y);
	        }
	    }
	    
	    if(e.type == SDL_KEYDOWN)
	    {
		    SDL_Keycode key = e.key.keysym.sym;
		    
		    
		    if(key == SDLK_c)
		    {
			    printf("Pressed c!");
		    }
	    }
	
	}
}
```

# References