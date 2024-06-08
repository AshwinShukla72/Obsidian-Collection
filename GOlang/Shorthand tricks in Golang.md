
#### Swapping Values between variables

```go
a, b := 123, 121

a,b = b, a
```

#### Defer a function call

```go
func myDeferFunc () {
 // Logic
}
defer myDeferFunc()

// Shorthand method, attach an anonymus function the defer
defer func() {
	// logic
}()
```

#### Check if value exists in a Map

```go

value, exists := myMap[Key]
if !exists {
	// Action on key not existing
}

// Shorthand
if value, exists := myMap[key]; !exists {
	// Action on key not existing
}
```

#### Loop Over Slices with Index and Value**

```go
// Long form
for i := 0; i < len(numbers); i++ {
    fmt.Println(i, numbers[i])
}

// Shorthand
for i, value := range numbers {
    fmt.Println(i, value)
}
```

#### Error handling 

```go
// Long form
result, err := someFunction()
if err != nil {
    // Handle the error
}

// Shorthand
if result, err := someFunction(); err != nil {
    // Handle the error
}
```

#### Create a Pointer to a Variable

```go
// Long form
var x int
ptr := &x

// Shorthand
ptr := new(int)
```

####  Anonymous Functions 
```go
// Long form
func add(x, y int) int {
    return x + y
}

// Shorthand kinda like arrow functions of JS
add := func(x, y int) int {
    return x + y
}
```