#### Structures
```ad-info
title: About structures
- Structures allow data to be stored in groups
	- They are similar to classes.
	- Each data point in the structure is called field
	- Storing data points in grops is more efficient
- Provides possibilities to associate functionality with structure 
	- Helps organize code and data.
```

#### Defining a #structure
> It can be termed as a lightweight class that does not support inheritance but supports composition.
```go
type Sample struct{
	field string
	a,b int
	c uint
}
```

#### Using structures

```go
package main

import . "fmt"
// can be declared inside main func or outside main func
type Sample struct {
	name        string
	age, height uint
	rollNo      int
}

func main() {
	data := Sample{"ashwin Shukla", 24, 187, 1603313016}
	Println("Name:", data.name)
	Println("Age", data.age)
	Println("Height", data.height)
	Println("Roll Number", data.rollNo)
}
```

#### Anonymous Structures
```go
anotherSample := struct {
		name        string
		age, height uint
		rollNo      int
	}{
		"Ravi Tiwari",
		29, 173,
		122345666,
	}
```
#### using structures with pointer method
```go
type User struct{
	FirstName string
	LastName  string
}
func (m *string) functionName()string{
	return m.StructValue
}

func main(){
	user := User{
		FirstName: "SomeName"
	}
	log.Println("Another User's firstName is:", user.functionName()) //prints SomeName
}
```

#### using structures
```go
package main

import . "fmt"

type Coordinate struct {
// creating a struct of coordinate
	x, y int
}
type Rectangle struct {
// creating another struct which inherits from coordinate class
	a Coordinate
	b Coordinate
}

func width(rect Rectangle) int {
	// Inheriting from Rectangle struct creaing width of a given rectangle
	return (rect.b.x - rect.a.x)
}
func length(rect Rectangle) int {
	// inheriting feom Rectangle struct creating a length of given rect
	return (rect.a.y - rect.b.y)
}

func area(rect Rectangle) int {
	return length(rect) * width(rect)
}
func permimeter(rect Rectangle) int {
	return (length(rect) + width(rect)) * 2
}
func printInfo(rect Rectangle) {
	Println("Width of rectangle:", width(rect))
	Println("Length of rectangle:", length(rect))
	Println("Area of rectangle:", area(rect))
	Println("Permimeter of rectangle:", permimeter(rect))
	Println()
}

func main() {
	rect := Rectangle{a: Coordinate{0, 7}, b: Coordinate{10, 0}}
	printInfo(rect)
}
```