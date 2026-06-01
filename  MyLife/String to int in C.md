```c
// C Program to convert string into integer manually
// using for loop
#include <stdio.h>
#include <string.h>

int main() {
    char *str = "4213";
    int num = 0;

    // Converting string to number manually using loop
    for (int i = 0; str[i] != '\0'; i++) {
        if (str[i] >= 48 && str[i] <= 57) {
            num = num * 10 + (str[i] - 48);
        }
        else {
            break;
        }
    }

    printf("The converted number is: %d", num);
    return 0;
}
```