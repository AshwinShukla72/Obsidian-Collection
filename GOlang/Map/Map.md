```ad-info
title: About
 - Maps are commonly used data structures that stores data in key value pairs
 - Extremely High performant when key is known
 - Data is stored in random order
```

```go
// myMap :=make(map[dataTypeForKey]dataTypeOfValue)
myMap := make(map[int]string)
myMap := map[int]string{
	1: "Ashwin",
	2: "Shukla",
	3: "Dum Dum",
}
```

#### Insert
```go
// myMap[Key] = value
myMap[4] = "Double Dum Dum"
```

#### Read
```go
find := myMap["Key"] // carries the value with that key
// If not found will not return anything
```

#### DELETE
```go
delete(myMap, "Key")
```
#### IF Exists
```go
key, found := myMap["Key"] // typeof found is bool and returns false when checked
if !found{
	Println("key value Not found") 
	return
}else{
	Println("Key found", key)
}
// Work around
 _ , found := myMap["Key"]
```


