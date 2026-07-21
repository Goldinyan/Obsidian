---
id: What isn't teached about memory
aliases:
Topic: How to free memory the right way.
Related:
  - "[[%Memory]]"
  - "[[%C]]"
Tags:
  - F
Date: 2026-02-07T17:35:00
Updated:
Source: https://www.youtube.com/watch?v=3HYUcGKDk2A&t=300s
---
# What isn't teached about memory

Lets say you have a linked list named action:

```c
typedef struct action {
  char *description;
  int state_delta;
  struct action *next;
} action_t;
```

When you don‘t need the programm anymore you will just free it using a loop for example.

```c
action_t *list = calloc(sizeof(action_t));


action_t curr = list;

while(curr =! NULL){
	action_t *next = curr->next;
	free(curr);
	curr = next; 
}
```

And voila we just leaked memory. Why you ask?
We allocated memory for the string in action_t. 
Now someone will say, okay lets just free the description as well:

```c
while(curr =! NULL){
	action_t *next = curr->next;
	free(curr);
	free(curr->description);
	curr = next; 
}
```

Now we got zero memory leaks, perfect. The problem is we have to remember to free this. What if there is also another struct in this one, with own values. Multiple nested structs in each other.
This is ***bad***.

# Linear Allocator

An interesting solution would be a linear allocator. 
This needs just a little more code, we just need to add a struct named Arena, and a single function.

```c
typedef struct {
  void *data; // buffer
  int capacity;
  int used;
} arena_t;
```

This is not a production ready implantation, it is just here to show you how it works.

Then we need a function, which allows us to write into that data buffer.

```c
void *arena_alloc(arena_t *arena, int size) {
  if (arena->used + size > arena->capacity) {
    return NULL;
  }
  void *ptr = (char *)arena->data + arena->used;
  arena->used += size;
  return ptr;
}
```

Now what we can do is:

```c
int size = sizeof(action_t) * 10;

arena_t arena = {
	.data = malloc(size);
	.capacity = size;
	// used is auto 0, because of the type of init
}
```


If we wanna free it, we just have to do:

```c
free(arena.data);
```