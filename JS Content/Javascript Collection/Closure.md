## Closure


>When a function “remembers” the variables outside of it, even if you pass that function else where.
> When a function remembers it’s lexical scope even when the function is executed outside of it’s lexical scope


```js
// Closure
var name = 'DODODODODODOOD';
(() => {
  return `Hello ${name}`; // Hello DODODODODODOOD
})();

// A better example of closure
function ask(question) {
  return function holdYourFunction() {
    console.log(question);
  };
}
var myQuestion = ask('What is closure');

console.log(myQuestion());

```
