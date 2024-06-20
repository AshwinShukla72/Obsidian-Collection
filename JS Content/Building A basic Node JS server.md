```js
// * Dependencies
const http = require('http');
const url = require('url');
const PORT = 3000;

var server = http.createServer((req, res) => {
  console.log('Hello from server');
  //! Get the URL and parse it
  let parsedUrl = url.parse(req.url, true);
  //! Get the Path
  let path = parsedUrl.pathname;
  //! Trimm the path
  let trimmedPath = path.replace(/^\+|\/+$/g, '');
  //! Get Query string as an Object
  //let queryStringObject = parsedUrl.query //! deprecated method
  //! Get the HTTP method
  let method = req.method;
  console.log(
    `Request received on path: ${trimmedPath} with method:${method} with this Query string parameters ${queryStringObject}`
  );
});

server.listen(PORT, () => {
  console.log(`Server listening on PORT: 3000`);
});

```