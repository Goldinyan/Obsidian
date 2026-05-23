Date: 2025-12-20
Tags: {
#F
[[%C]]
[[%Basics]]
[[%Functions]]
[[%Loops]]
[[%Computer Science]]
}

## Functions

```c
float add(int a, int b) {
    return (float)(a + b); //cast to float
}

//there can also be one line Functions

if(x > 10) return ERROR;

//is the same as

if(x > 10){
	return ERROR;
}
```

---

## Loops

```c

for(int i = 0; i < 5; i++){
	printf("%d\n", i);
}

int i = 0
while(i < 5){
	printf("%d\n", i);
	i++;
}

int y = 0
do{
	printf("%d\n", i);
	y++;
}while(y < 5)

```
---
## Void

```c
int getInteger(void){
	return 42; 
	//takes nothing, no value 
	//btw null is a value
}

void printIntenger(int x){
	printf("this is an int %d", x)
	//returnes no value
}
```
