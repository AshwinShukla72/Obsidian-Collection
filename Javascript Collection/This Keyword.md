```ad-info
Every* function, while executing has a reference to it's current execution context, the reference is called 'this'
```

> The this key‐word. It’s a special identifier keyword that’s automatically defined in
the scope of every function

#### Explicit Binding
```js
function foo(){
	console.log(this.bar)
}
var bar = "Bar 1"
var obj = {bar :"Bar 2"}

foo() // "Bar 1"
foo.call(obj) // "Bar 2" -> call foo but use obj for reference
```

#### Hard Binding
```js
function foo(){
	console.log(this.bar)
}
var obj = { bar : "bar" }
var obj2 = {bar: "bar" }

var orig = foo

foo = function(){orig.call(obj)}

foo() //bar
foo.call(obj)
```

#### New Binding
```js
function foo(){
	this.baz = "baz"
	console.log(this.bar + "" + baz)
}
var bar = "bar"
var baz = new foo()
```
