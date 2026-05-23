Date: 2025-12-20
Tags: {
#W
[[%C]]
[[%Basics]]
[[%Enums]]
[[%Computer Science]]
}



## Enums



Enums define named integer constants.  
```c
enum Color {
    RED,
    GREEN,
    BLUE
};

enum Color c = GREEN;
```
- Values start at 0 by default and increase by 1.  
- You can assign custom values:  
  ```c
  enum Status { OK = 200, ERROR = 500 };
  ```
