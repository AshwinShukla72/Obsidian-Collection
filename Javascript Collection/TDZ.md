### TDZ

> TDZ stands for the temporal deadzone
>#####  the term to describe the state where variables are un-reachable. They are in scope, but they aren't declared.

```js
{
  // This is the temporal dead zone for the age variable!
  // This is the temporal dead zone for the age variable!
  // This is the temporal dead zone for the age variable!
  // This is the temporal dead zone for the age variable!
  let age = 25; // Whew, we got there! No more TDZ
  console.log(age);
}

```