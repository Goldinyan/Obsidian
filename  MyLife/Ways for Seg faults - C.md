
Date: 2026-01-02  
Tags: { 
#W 
[[%C]]
[[%Memory]]
[[%Pointers]]
}

## 1. Accessing null pointer

```c
int *p = NULL;
*p = 10;   // seg fault

// p has the adress 0x0, is never mapped

// *p is the same as p[0]
// a[b] = *(a + b)
// If b = 0, 
// a[0] = *(a + 0) = *a

```


## 2. Array out of bounds

```c
int a[3] = {1,2,3};
a[10] = 5;   // seg fault (undefined behavior)
```


## 3. Pointer-Arithmetik beyond allowed location

```c
int a[5] = {0};
int *p = a + 100; // a + 100 -> 100 * sizeof(int) further
// 100% out of mapped memory
*p = 1;      // seg fault
```


## 4. Use-after-free

```c
int *p = malloc(sizeof(int));
free(p);
*p = 10;     // seg fault
```


## 5. Double free

```c
int *p = malloc(4);
free(p);
free(p);     // seg fault
```



## 6. Writing in readonly-Memory (String-Literal)

```c
char *s = "hello"; 
s[0] = 'H';   // seg fault
// Why this is can be read in [[Readonly-Memory - C]]
```


## 7. Dereferenzieren eines uninitialisierten Pointers

```c
int *p;   // uninitialized, contains garbage
// random bit garbage
// thinks garbage is address 
// accessing not mapped memory
*p = 5;   // seg fault
```


## 8. Stack overflow, through infinite recursion

```c
void f(void) {
    f();   // eventually seg fault
}
```



## 9. Access of already destroyed Variable (dangling pointer)

```c
int *make_ptr(void) {
    int x = 10;  // x only lives in the stack of the func
    // if it ends, the, the stack frame gets destroyed
    // &x shows to not existing memory
    return &x;   // returns pointer to dead stack memory
}

int main(void) {
    int *p = make_ptr(); // shows to unmapped stack value
    *p = 5;       // seg fault
}
```

The right way would be one of these:

```c
int *make_ptr(void) {
    int *p = malloc(sizeof(int)); 
    // Memory lives further than function stack
    *p = 10;
    return p;
}

int main(void) {
    int *p = make_ptr();
    *p = 5;   // valid
    free(p);
}

// OR

int *make_ptr(void) {
    int *p = malloc(sizeof(int));
    *p = 10;
    return p;
}

int main(void) {
    int *p = make_ptr();
    *p = 5;   // valid
    free(p);
}
```
