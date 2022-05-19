```ad-info
title: defintion
- Arrays are a way to store multiple pieces of smae type of data
	- Data is stored consecutively in an _*array*_ of data
	- Each piece is called and _*element*_ 
- To access an element of an array, you need the index of the array 
- *Arrays are fixed size and cannot be resized*
```

#### Creating an array
```go
var myArray [3]int // name [array size]typeOfData
myArray[0] = 1

myArray[1] = 2

myArray[3] = 3 // will throw an error of array out of bounds


myArray := [3]int{7,8,9} // by compound assignment method
myArray := [...]int{12,4,5,6,3,7,7} // when size of array is negotiable
```
[[Dynamic Arrays]]
```go
package main

import (
	"fmt"
	_ "reflect"
)

type Product struct {
	productName string
	price       int
}

func main() {
	productArray := [4]Product{
		{
			productName: "Apple", price: 20,
		}, {
			productName: "Oranges",
			price:       12,
		}, {
			productName: "Bananas",
			price:       21,
		},
	}
	total := 0
	product5 := Product{
		productName: "Lemons",
		price:       100,
	}
	productArray[3] = product5
	for i := 0; i < len(productArray); i++ {
		fmt.Println("Product:", productArray[i].productName, ",Price:", productArray[i].price)
		total += productArray[i].price
	}
	fmt.Println("Total Price of products:", total)
}

```

![[Ranges]]