Date: 2025-12-21
Tags: {
#N
[[%Command]]
[[%Terminal]]
}


# Overall usefull Commands



--- 

`| less` sends the output of a command into the `less` pager.  
This lets you scroll through long output instead of having it flood the terminal.  
You can move with arrow keys, search with `/text`, jump to start with `g`, jump to end with `G`, and quit with `q`.   
It’s useful for commands that produce many lines, like `strings`, `xxd`, or `objdump`.
- Space – eine Seite weiter
- b – eine Seite zurück
**Example:**

```
strings program | less
```

This shows all extracted strings in a scrollable, searchable view.

---


# References