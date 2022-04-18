```ad-info
- Slices are companion types that work with arrays
- They enable "view" into arrays
	- "Views" are dynamic & not of fixed size
- Functions can accept a slice as a function parameter
	- Any size array can be operated upon via slice.  
```


```go
myslice := []int{1,2,4}
```

```ad-warning
Slice syntax can create slices from specific elements in an array or other slice `slice[a:b]`, "a" is the starting index and "b" is the ending index.
```
```go
// Creating a slice
myArray := [...]int{1,2,3,4,5,5,6,7,8,9,11}
slice1 := myArray[0:5] // start at zeroth element of the array and end at the 5th
```

>   **Slices are used to create arrays that can be extended**
>   The `append()` function only adds to a slice and with the added values a new slice has to created

```go
// taking the above example
slice2 := append(slice1, 1,2,3,4) // [1,2,3,4,5,1,2,3,4]
```
> ==A slice can be extended with other slice==
```go
b := append(slice1, slice2...)
// and be further extended with other slices
b = append(b, slice...)
```
![[Prealocating slices]]

> ==Slices always require underlying array==

```go
package main

import (
	. "fmt"
	_ "reflect"
)
// function that prints all elements of a slice by iteration
func printSlice(title string, slice []string) {
	Println()
	Println("====", title, "====")
	for i := 0; i < len(slice); i++ {
		element := slice[i]
		Println(element)
	}
}
func main() {
	route := []string{"Grocery", "Department Store", "Salon"}
	printSlice("route 1", route)
	// adding another element in the slice
	route = append(route, "Home")
	printSlice("route 2", route)
	Println()
	Println("====","Places visited","====")
	Println(route[0], "=> Visited")
	Println(route[1], "=> Visited")
	Println(route[3], "=> Visited")
	Println(route[2], "=> Not Visited")
	// adding another route through the append method on slice
	route = append(route,"Fish Market")
	printSlice("route 3", route)
}

```

![[MultiDimensional Slices]]

![[Ranges]]