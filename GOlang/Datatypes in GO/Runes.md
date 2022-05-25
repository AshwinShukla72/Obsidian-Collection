- ###### Text is represented using **Rune Type**
- Rune is an alias for int32(32 bit integer)
- Will print Numeric value unless formatting is specified.
- A rune can represent any symbol (Emoji,Letters or Numbers)

**Important:** _Runes Require use of single quotes_
Example: 
```go
var (
    firstInitial = 'A'
    lastInitial = 'B'
    emjoi ='😃' // Val 128515
)
fmt.Println(firstInitial) // Prints ASCII value of A
```