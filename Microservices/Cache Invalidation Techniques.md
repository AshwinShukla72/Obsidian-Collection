1. **Manual/Programmatic Invalidation**
	1. Using the code which changes the data, to invalidate the cache, when data has been updated
2. **Time-to-Live (TTL) Invalidation**
	1. This strategy allocates a predetermined time interval to each item stored in the cache (can be done through a Cron which makes sure that after 3 days the cache is cleared)
3. **Event-Based Invalidation**
	1. When a significant event occurs, such as a data update, a system can dispatch a message or signal to the cache, indicating that certain data has been modified. The cache can then proceed to invalidate the pertinent data. This approach requires a messaging/event infrastructure.
4. **Version-Based Invalidation**
	1. Updating the data when document's version has been changed
5. **Cache Keys Invalidation**
	1. If a specific data is changed, the only the cache key pointing to that data is invalidated, allowing cache for other places to work
6. **Layered Invalidation**
	1. Given that the data is present in layers i.e. some data is fetched from one table and other from other table, if data from one table is altered only cache for that data needs to be altered
7. **Lazy Invalidation**
	1. In this strategy, the cache isn’t immediately invalidated after an update. Instead, it’s marked as “invalid,” and new data is fetched only when someone attempts to access the invalid data. This avoids unnecessary invalidations but may introduce slight latency in the first query after the update.