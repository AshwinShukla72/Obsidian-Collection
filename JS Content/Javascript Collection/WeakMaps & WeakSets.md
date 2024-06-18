
```JS
// Weak Set
const userSessions = new WeakMap();

let user1 = { name: 'Alice' };
let user2 = { name: 'Bob' };

userSessions.set(user1, { lastLogin: '2024-06-19' });
userSessions.set(user2, { lastLogin: '2024-06-18' });

console.log(userSessions.get(user1));

// Weak Set
const activeTasks = new WeakSet();

let task1 = { id: 1 };
let task2 = { id: 2 };

activeTasks.add(task1);
activeTasks.add(task2);
```

```ad-info
- **WeakMap**: Used when you need a map-like structure where keys are objects and you want the entries to be garbage-collected when there are no other references to the keys.

- **WeakSet**: Used when you need a set-like structure to store objects and want them to be garbage-collected when there are no other references to those objects.

```

```ad-summary
WeakMap and WeakSet are similar to sets and maps but with lesser methods attached to them

- WeakMap only has delete, get, has & set methods
- WeakSet has add, delete and get methods


Both of them are used to check if the value exists rather than working on it, both are short lived, the values they are referencing to is made void they can be garbage collected, they will hold less storage overtime
```
