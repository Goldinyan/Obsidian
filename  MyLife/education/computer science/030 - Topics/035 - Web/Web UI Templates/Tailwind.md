Date: 2025-12-20
Tags: {
#W
[[%WebDev]]
[[%Computer Science]]
[[%Config]]
}

# Tailwind

## How to import Plugins:

In Tailwind it was possible to import plugings in the *tailwind.config.js*, like this:

```ts
export default {
	plugins: [
		require("daisyui"),
		require("flowbite/plugin") // ==> for Flowbite
		require("tailwindcss-animate") // ==> for Shadcn
	],
	darkMode: ["class"] // ==> for Shadcn
	prefix: "tw",
}
```

But after switching to Tailwind v4, its now required to import Plugins in the  *global.css*:

```css
@import "tailwindcss";
@plugin "daisyui"; /* To add plugins  */
```



# References


