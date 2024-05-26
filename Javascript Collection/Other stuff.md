
> [!NOTE]
> The JavaScript language is transitioning from being a single-threaded language to being a multithreaded language. The Atomics object, for example, provides mechanisms to coordinate communication across different threads, while instances of ==SharedArrayBuffer== can be written to and read from across threads. That said, as of this writing, multithreaded JavaScript still hasn’t caught on within the community. ==JavaScript today is multithreaded==, but it’s still the nature of the language, and of the ecosystem, to be single-threaded.

#### Creating My Own Map method for Arrays
```JS
Array.prototype.myMap = function (callbackFunction) {
  if (typeof callbackFunction !== "function") {
    throw new Error("Second argument must be a function");
  }

  const mappedArray = [];
  for (let i = 0; i < this.length; i++) {
    mappedArray.push(callbackFunction(this[i], i, this));
  }
  return mappedArray;
};


```