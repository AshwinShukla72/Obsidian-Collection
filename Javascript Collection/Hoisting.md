```ad-info
JavaScript Hoisting refers to the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.
```

```js
function foo(){
	return `Function ${bar()} Hoisted` 
}

function bar(){
	return `bar`
}

foo() // Function bar Hoisted

```