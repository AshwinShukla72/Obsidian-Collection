_**Range keyword creates a iterator for us **_ 

```go
// Iterating over elements of a slice
func main() {
	slice := []string{"Hello","World","!"}
	for index, element := range slice{
		Println(index, element)
		for _, ch:= range element{
			Printf("%q\n",ch)
		}
	}
}
```

- Range method is used for iteration using for loop
- It takes two params index and element and iterates through them
- Can be used with arrays and iterate over them

#arrays
```go
	myArray := [4]string{"ashwin", "shukla", "is", "dumb"}
	for _, element := range myArray {
		Println(element)
		for _, element := range element{
			Println(string(element))
		}
	}
```