> Go uses for keyword for repetion

```go
for i:= 0; i<10; i++{
 // ... loops bitch
}
```

Looping can *stalled, taken out of execution* & *continued*  with use of `break` and `continue` .

```go
for i:= 0; i<10; i++{
	if i == 5{
		Println(i)
		continue
	}
	if i > 10{
		break
	}
}
```

- ![[Ranges]]