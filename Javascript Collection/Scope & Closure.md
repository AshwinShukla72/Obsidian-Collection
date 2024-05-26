## What is scope?
By definiton #scope of anything means where to find stuff

#### Compiling Code
A classic compiler theory a program is processed in 3 steps => 
- #### Tokenization/Lexing 
	 Breaking up a sequence of strings into pieces such as words, keywords, phrases, symbols and elements called tokens 
- #### Parsing
	Taking the above generated stream and it into a tree of nested elements and thus generating Abstract Syntax Tree.
- #### Code generation
	Taking the AST generated above and turning it into executable code


> The common programming compilation happens in the above 3 phases but for JS it occurs in 2 namely parsing/compilation and then compilation.

JS specifically does not require the compilation policy as above rather that the behaviour observed in only possible through the mechanism of ==compile-then-execute== .

```js
function greetings(){
	 var greetings = "Joshua";
	{ 
		greeting = "Nameless";
		 let greeting = "jsjsjsjsj";
		console.log(greeting) 
	} 
}
 greetings()
}
```

In the above program the JS engine will start handing out problems in the code by telling about the reference error and duplicate error for the above code.

This can only be accomplished if the code as compiled and the scopes for each case were calculated. Thus, code is parsed before execution

> Compilation creates a map of all lexical scopes that lays out what the program will need while it executes.
> This is to understand that scopes are identified during compilation but not used until runtime.

#### Scoping Rule
Inner scope can access variables initialized in an outer scope, but not vice versa.
![[Block Scoping]]

 ![[Closure]]






