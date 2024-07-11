
## Operating Without Root Privileges

```ad-attention

Creating a dedicated user for your Node.js application restricts potential damage in the event of a compromise.

```Dockerfile
FROM node:18-alpine  

RUN addgroup adx && adduser -S -G adx adx  

WORKDIR /usr/src/app/backend  

COPY package*.json ./  

RUN npm install  

COPY . .  

RUN npm run build  

USER adx  

EXPOSE 5000  

CMD "npm", "start"
```

## Implementing Secure HTTP Headers with Helmet in Express

```ad-info

Secure HTTP headers are crucial for protecting your app from various types of attacks like XSS, clickjacking, and other cross-site injections.


```JS
// In Express

const helmet = require('helmet');  
  
app.use(helmet({  
// Custom helmet configuration here  
}));


// In Hono

import { Hono } from 'hono' 
import { secureHeaders } from 'hono/secure-headers'

const app = new Hono() 
app.use(secureHeaders())
```

## Rate Limiting

Rate limiting is essential for protecting your application against brute-force attacks and DDoS by limiting the number of requests a user can make in a given timeframe.

```JS

// In Hono
const limiter = rateLimiter({
  windowMs: 15 * 60 * 1000, // 15 minutes
  limit: 100, // Limit each IP to 100 requests per `window` (here, per 15 minutes).
  standardHeaders: "draft-6", // draft-6: `RateLimit-*` headers; draft-7: combined `RateLimit` header
  keyGenerator: (c) => "<unique_key>", // Method to generate custom identifiers for clients.
 store: new RedisStore({
		sendCommand: (...args: string[]) => client.sendCommand(args),
	}),
});
```
## Minimizing Error Details

Ensure that production environments do not expose stack traces or detailed error messages to users.

```JS

app.use((err, req, res, next) => {
  res.status(500).json({ error: "Internal Server Error" });
});
```


## Embracing HTTPS-Only Policy

Redirect all HTTP traffic to HTTPS and ensure that cookies are set with the <mark style="background: #FF5582A6;">Secure</mark> attribute.
```js
app.use((req, res, next) => {
  if (!req.secure) {
    return res.redirect(`https://${req.headers.host}${req.url}`);
  }
  next();
});
```