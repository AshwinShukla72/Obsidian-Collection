```ad-info

This scope restricts the variable that is declared inside a specific block, from access by the outside of the block.
```

> Inner scope can access variables initialized in an outer scope, but not vice versa.

```js
function formatString(str) {
  {
    let prefix, rest;
    prefix = str.slice(0, 3);
    rest = str.slice(3);
    str = prefix.toUpperCase() + rest;
  }
  if (/^FOO:/.test(str)) {
    return str;
  }
  return str.slice(4);
} 

// when block scoping should be used
for(let i =0; i<10; i++){
 // .... Here the i is declared for the for loop and scoped for only this loop
}

// where using var is better 
// when you want a variable declaration to escape an unintentional block
const routeFunc = async (req, res) => {
  try {
    var id = await User.findOne({ where: { id: id } });
  } catch (err) {
    return res.send(err);
  }
};
```

