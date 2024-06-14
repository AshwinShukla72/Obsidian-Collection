```ad-summary
- Take advantage of the locality of reference principle: recently requested data is likely to be requested again.
- Exist at all levels in architecture, but often found at the level nearest to the front end.
```

## Types

- Application Server Cache => 
	- *Stores frequently queried data, static webpages, so that it can be frequently retrieved*
- Distributed Cache =>
	- *A distributed cache works by spreading data across multiple servers or locations. Allowing data retrieval even if one server is down.*
- Global Cache =>
	- *A global cache is a single cache space that all parts of an application refer to, ensuring that everyone has access to the same data, no matter where they are in the system*

## Cache invalidation

- Keep cache coherent with the source of truth. Invalidate cache when source of truth has changed.
- **Write-through cache**
    - Data is written into the cache and permanent storage at the same time.
    - **Pro** -> Fast retrieval, complete data consistency, robust to system disruptions.
    - **Con** -> Higher latency for write operations.
- **Write-around cache**
    - Data is written to permanent storage, not cache.
    - **Pro** -> Reduce the cache that is no used.
    - **Con** -> Query for recently written data creates a cache miss and higher latency.
- **Write-back cache**
    - Data is only written to cache.
    - Write to the permanent storage is done later on.
    - **Pro** -> Low latency, high throughput for write-intensive applications.
    - **Con** -> Risk of data loss in case of system disruptions.


- ![[Cache Invalidation Techniques]]



