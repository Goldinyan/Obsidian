Date: 2025-12-20
Tags: {
#F
[[%C]]
[[%Basics]]
[[%Array]]
[[%Computer Science]]
}




## Array Length & Pointer

```c
int main(void) {

  int nums[5] = {4, 7, 10, 3, 6};
  int length = sizeof(nums) / sizeof(nums[0]);
  
  return 0;
}

float getAverage(int arr[], int lenght){
  int sum = 0;
  for(int i; i < lenght; i++){
    sum += arr[i];
  }
  return (float)sum / lenght;
}
```


`sizeof(nums)` gives the total number of bytes of the array, while `sizeof(nums[0])` gives the size of a single element. Dividing the two yields the element count. When you pass an array to a function, it decays into a pointer, so the compiler no longer knows its length. That is why you must pass the length as a separate parameter. Inside a function like `foo(int *arr)`, the parameter is just a pointer, and `sizeof(arr)` only returns the size of the pointer itself, for example 8 bytes on a 64‑bit system, not the size of the original array. 

```c
int arr[5] = {1,2,3,4,5};
int *p = arr

// *p = (1)
// *(p + 1) = 2
```
A pointer in C knows the address it points to and lets you read or write the value there, but it does not store the length of the memory block. Arrays in their own scope carry size information through `sizeof`, but once passed to a function they decay into pointers, and `sizeof` then only returns the size of the pointer itself. That’s why the array length must always be tracked or passed separately.
