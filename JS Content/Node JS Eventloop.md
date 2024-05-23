#eventloop
> Works the same way as JS event loop.

==`process.nextTick()` this function is run everytime eventloop is run once==

After every tick, the runtime performs checks
1. If there are any pending `setTimeout()`,`setInterval()` or `setImmediate()` function calls left.
2. If there are any pending OS tasks.
3. If there are any pending long running tasks. 

- ##### setImmediate()
	- Run in asynchronous runtime, whenever a task has to be run immediately. `setImmediate() = setTimeout(()=>{},0)`