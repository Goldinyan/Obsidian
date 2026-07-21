---
id: "Array vs Pointer - C"
aliases:
Topic:
Related:
Tags:
  - w
Date:
Updated:
Source:
---
# Array vs Pointer - C

Arrays are just pointer with pointer arithmetic.

```c
#include <stdint.h>
#include <stdio.h>

typedef int8_t i8;
typedef int16_t i16;
typedef int32_t i32;
typedef int64_t i64;

int main() {
  i32 nums[] = {1, 2, 3, 4, 5};

  for (i32 i = 0; i < 5; i++) {
    *(nums + i) = 5 - i; // this reverses the array in place
    nums[i] = 5 - i;     // also this
    i[nums] = 5 - i; // and this, because in C, a[b] is defined as *(a + b), so
                     // i[nums] is the same as nums[i]
  }

  printf("%p\n", (nums)); // the address
  printf("%d\n", *(nums + 1)); // nums[1] so 4
  return 0;
}
```