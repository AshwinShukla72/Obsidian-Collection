### How to declare variables in Go
```ad-info
A variable is a alias for a data block in memory
```
Variables can be declared in GO in a number of ways

```go
// create a variable named name of type string
var name string = "Ashwin";

// this is compound assignement method
// this basically declares and assigns the variables
firstName, lastName := "Ashwin", "Shukla" // access level is scoped inside the function it is created inside

// block assignement method
// can be declared and used outside main functions
var (
    firstInitial = "A"
    lastInitial = "B"
)
// const is used to declare varibles that will not be reassigned
// using block assignement method outside main function provides access globally
const (
	Admin = 10
	SE1   = 20
)

```
```ad-warning
variables created using `var` and `const` outside the function can be accessed globally
```

