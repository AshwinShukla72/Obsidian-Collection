### Functions

> Functions are a collection of procedures

```js
function addfavoriteBooks(bookName) {
  if (!bookName.includes('Great')) favoriteBooks.push(bookName);
  printFavoritebooks(favoriteBooks);
  return favoriteBooks;
}
function printFavoritebooks(favoriteBooks) {
  return console.log(favoriteBooks, favoriteBooks.length);
}
var favoriteBooks = [];

addfavoriteBooks('A song of Ice and Fire');
addfavoriteBooks('the Great Gatsby');
addfavoriteBooks('Crime and Punsihment');
addfavoriteBooks('Great Expectations');
addfavoriteBooks("You Don't know JS");
addfavoriteBooks('the Name is DOTA');

// formal declaration
function boo(param) {
  // formal declaration of a variable called param
  return console.log(param);
}

```

![[Hoisting]]