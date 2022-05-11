## Introduction
This application is built solely to understand and use mongoDB to create CRUD API, and use YAML files to design routes.
In this application mongoDB is used through a docekr container, and connecting to it through mongoose ODM. #nodejs 

## Requirements
- `docker 20.10.14`
- `node js >=14.19`
- `express >= 4.17.3`
- `nodemon`
- `mongoose: 6.3.1`

## Installation
`npm i express mongoose mongodb`

## Folder Structure


## Docker Commands
```bash
docker run --name mongo-express -dit -p 27017:27017 --rm mongo
```

- ==This docker command will create a docker container with name of mongo-express set port to 27017, and remove all the data inside when the container will be closed==

```bash
docker exec -it mongo-express mongo
```

- ==Run the docker container in executable mode, allowing us to use it through bash command patterns==

```bash
docker pause containerID
```

- ==Stop the container keeping the previous data intact==

```bash
docker stop containerID
```

## Server setup
```js
const express = require('express')
const mongoose = require('mongoose')
const app = express()

// Middlewares

app.use(express.json())

app.use(express.urlencoded({ extended: false }));

app.use(express.text())

// Mongo Models
const config = require('./config/db');
const PORT = 4000; // set it as environment variable
// Create an IIFE that connects to mongoDB container on every reload
(async function () {
  await mongoose
    .connect(
      config.DB,

      {
        useNewUrlParser: true,

        useUnifiedTopology: true,
      }
    )

    .then(() => {
      console.log(`connected to ${config.DB}`);
    })

    .catch((err) => {
      console.log('Something went wrong', err);
    });
})();

app.listen(PORT,()=>{
	console.log(`Server Running on port:${PORT}`)
})

```


## Creating A User Module
