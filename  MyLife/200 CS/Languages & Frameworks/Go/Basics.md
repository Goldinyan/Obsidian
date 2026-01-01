
```go
package main

  

import "fmt"

  

func main() {

fmt.Println("Hello World!")

  

var name = "Ansgar Seifert"

x := 2

  

fmt.Println(name)

fmt.Println(x)

  

var a string

var b int

var c bool

  

fmt.Println(a, b, c)

  

var d, e = 6, "Hello"

  

fmt.Println(d, e)

  

const PI float32 = 3.14

fmt.Println(PI)

  

var arr1 = [3]int{1, 2, 3}

arr2 := [5]int{4, 5, 6, 7, 8}

  

var arr3 = [...]int{1, 2, 3}

arr4 := [...]int{4, 5, 6, 7, 8}

  

fmt.Println(arr1)

fmt.Println(arr2)

fmt.Println(arr3)

fmt.Println(arr4)

  

var arr5 = [...]int{1, 3, 5, 7, 9}

arr5[2] = 50

  

fmt.Println(arr5)

  

//man kann es auch nicht initialisen

  

var arr6 = [5]int{}

fmt.Println(arr6)

  

//oder halb

  

arr7 := [5]int{2, 4}

fmt.Println(arr7)

  

//kann auch nur bestimmt Stellen init

  

arr8 := [8]int{2: 20, 5: 1}

fmt.Println(arr8)

  

//len()

  

fmt.Println(len(arr8))

  

// https: //www.w3schools.com/go/go_slices.php

  

num := 20

if num >= 10 {

fmt.Println("Num is more than 10.")

if num > 15 {

fmt.Println("Num is also more than 15.")

}

} else {

fmt.Println("Num is less than 10.")

}

  

day := 4

  

switch day {

case 1:

fmt.Println("Monday")

case 2:

fmt.Println("Tuesday")

case 3:

fmt.Println("Wednesday")

case 4, 5, 6, 7:

fmt.Println("Thursday or else")

  

}

  

adj := [2]string{"big", "tasty"}

fruits := [3]string{"apple", "orange", "banana"}

for i := 0; i < len(adj); i++ {

for j := 0; j < len(fruits); j++ {

fmt.Println(adj[i], fruits[j])

}

}

  

fmt.Println(myFunction(1, 2))

_, z := myFunction2(5, "Hello") //ignores _

  

fmt.Println(z)

  

fmt.Println(factorial_recursion(4))

  

var pers1 Person

var pers2 Person

  

// Pers1 specification

pers1.name = "Hege"

pers1.age = 45

pers1.job = "Teacher"

pers1.salary = 6000

  

// Pers2 specification

pers2.name = "Cecilie"

pers2.age = 24

pers2.job = "Marketing"

pers2.salary = 4500

  

// Access and print Pers1 info

fmt.Println("Name: ", pers1.name)

fmt.Println("Age: ", pers1.age)

fmt.Println("Job: ", pers1.job)

fmt.Println("Salary: ", pers1.salary)

  

// Access and print Pers2 info

fmt.Println("Name: ", pers2.name)

fmt.Println("Age: ", pers2.age)

fmt.Println("Job: ", pers2.job)

fmt.Println("Salary: ", pers2.salary)

  

// Print Pers1 info by calling a function

printPerson(pers1)

  

// Print Pers2 info by calling a function

printPerson(pers2)

  

changeName(&pers1, "Anna")

  

//var a = map[KeyType]ValueType{key1:value1, key2:value2,...}

//b := map[KeyType]ValueType{key1:value1, key2:value2,...}

  

var y = map[string]string{"brand": "Ford", "model": "Mustang", "year": "1964"}

u := map[string]int{"Oslo": 1, "Bergen": 2, "Trondheim": 3, "Stavanger": 4}

  

fmt.Println(y)

fmt.Println(u)

  

var g = make(map[string]string) // The map is empty now

g["brand"] = "Ford"

g["model"] = "Mustang"

g["year"] = "1964"

// g is no longer empty

// func make(t Type, size ...int) Type

// The make built-in function allocates and initializes an object of type slice, map, or chan (only). Like new, the first argument is a type, not a value. Unlike new, make's return type is the same as the type of its argument, not a pointer to it. The specification of the result depends on the type:

  

// Slice: The size specifies the length. The capacity of the slice is equal to its length. A second integer argument may be provided to specify a different capacity; it must be no smaller than the length. For example, make([]int, 0, 10) allocates an underlying array of size 10 and returns a slice of length 0 and capacity 10 that is backed by this underlying array.

// Map: An empty map is allocated with enough space to hold the specified number of elements. The size may be omitted, in which case a small starting size is allocated.

// Channel: The channel's buffer is initialized with the specified buffer capacity. If zero, or the size is omitted, the channel is unbuffered.

  

h := make(map[string]int)

h["Oslo"] = 1

h["Bergen"] = 2

h["Trondheim"] = 3

h["Stavanger"] = 4

  

fmt.Printf("a\t%v\n", g)

fmt.Printf("b\t%v\n", h)

  

}

  

func changeName(pers *Person, newName string) {

pers.name = newName

}

  

//doesnt make copy, it changes

  

func printPerson(pers Person) {

fmt.Println("Name: ", pers.name)

fmt.Println("Age: ", pers.age)

fmt.Println("Job: ", pers.job)

fmt.Println("Salary: ", pers.salary)

}

  

func myFunction(x int, y int) int {

return x + y

}

  

func myFunction2(x int, y string) (result int, txt1 string) {

result = x + x

txt1 = y + " World!"

return

}

  

func factorial_recursion(x float64) (y float64) {

if x > 0 {

y = x * factorial_recursion(x-1)

} else {

y = 1

}

return

}

  

type Person struct {

name string

age int

job string

salary int

}
```
