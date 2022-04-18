
## let, const and var
let, const and var are keywords used to declare variables in javascript.
```ad-note
Variables are representation of some place in memory / variables are aliases for memory address
```
> `let` and `const` declarations are both block-scoped which means they are only accessible within the `{}` surrounding them. var, on the other hand, doesn't have this restriction.
> ==**The const keyword is to create a variable which cannot be reassigned**==


The usage of const to tell the user that this value should not be re-assigned.

```js
 const arr = [12,2,3,5,5,6]
```
>
>here the variable array doesn’t hold the values of the array, rather it holds the constant reference to the array,

```ad-warning
Assigning an object or array as a constant means that value will not be able to be garbage collected until that constant’s lexical scope goes away, as the reference to the value can never be unset. That may be desirable, but be careful if it’s not your intent!
```
