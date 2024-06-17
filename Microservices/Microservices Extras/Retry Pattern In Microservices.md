An application that connects to other services over the internet needs to be designed to handle brief periods when those services might not be available, this is called being **resilient** 

```ad-important
While designing any system it is essential to make it resilient against such failures.
```

## What is failure?

- Slow Response / No Response
- Response in incorrect format
- Response with incorrect Data

# Retry Methodology:
A process of automatically repeating a request in case any failure is reported or detected

The only caveat when it comes to retrying is that multiple requests to the same resource should have the same effect as making a single request.

> In REST APIs, `GET`, `HEAD` and `OPTIONS` methods generally do not change the resource state on the server and hence are mostly retry able.

## When should we retry a request?

The general idea is that if an upstream request fails, we immediately try again, and probably the second request will succeed. However, this will not always benefit us. The actual implementation should include a delay between the subsequent requests.

## The problem with normal retries

```ad-example
Consider what happens when we get 100,000 concurrent requests & all hosts of the upstream service are down at that instance. If we were to retry immediately, these 100,000 failed requests would retry immediately on a static interval. The 100,000 request will be combined with the new incoming requests when even these fail the the service will be overwhelmed with number of request increasing exponentially, leading to what will is called the thundering herd problem 🐂🐂🐂🐂🐂

```

# Backoff
The wait time between a request and its subsequent retry is called the backoff, with backoff the amount of time between requests increases exponentially as the number of requests increases

A simple backoff implemetation is not the best solution as multiple request will be retried after the same time, resulting in constant retries of to the resource even after multiple retries.

# Jitter?
Jitter is the process of breaking this synchronization by increasing or decreasing the backoff delay to further spread out the load, Jitter introduces randomness to the retries i.e. on the maximum server load the above 4 requests will be retried at different positions _the order of request retires will be randomized_ if the requests are retriable

![[Pasted image 20240617235017.png]]
```ad-seealso
[Exponential Backoff and Jitter](https://aws.amazon.com/blogs/architecture/exponential-backoff-and-jitter/)
```


