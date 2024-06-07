JavaScript has **7 primitive types**:

-  **string** (sequence of characters)
-  **number** (floating point is the only number type)
-  **bigint** (for huge numbers)
-  🔝**boolean** (logical data type with two values)
-  **undefined** (assigned to variables that have just been declared)
-  **symbol** (unique values)
-  **null** (points to a nonexistent object or address)

Alongside those **primitive types** there are **Primitive Wrapper Objects**=:

- **String** (for the string primitive)
- **Number** (for the number primitive)
- **BigInt** (for the bigint primitive)
- **Boolean** (for the boolean primitive)
- **Symbol** (for the symbol primitive)

Let’s clear up the difference between **primitive types** and **primitive wrapper objects** so you don’t get confused if you should use the lowercase `string` or capitalized `String` as a type.

JavaScript converts **primitive types** to **primitive wrapper objects** behind the scenes so we can use their methods.

This is because methods like `toUpperCase` extend the `String` object.

The reason we don’t use **primitive wrapper objects** is because it’s more work to get the value out of the object and we could get unexpected results if we pass an object to something expecting a **primitive** value.