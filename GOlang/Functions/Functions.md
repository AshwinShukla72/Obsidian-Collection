## Functions in GO

```ad-info
title: Definition of function
Functions generally are blocks of code in a program which give the user the ability to reuse the same code for varying conditions, *Ultimately saving space* 
```


```go
func nameOfFunction(x int) int { // (params and type) output type
	newName := "Seraphine"
	Println(x) // Operation on input
	
	Println(newName) // prints "seraphine"
	
	functionName(&newName) //passing a reference to the variable
	
	Println(x) // prints Josephine
}
```

#### Functions using pointers
```go
func functionName (s *string){
	name:= "Josephine"
	*s = name
}
```
#### [[Variadic Functions in GO]]



