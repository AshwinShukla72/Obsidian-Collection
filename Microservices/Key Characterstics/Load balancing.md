
#loadbalancing

```ad-abstract
Method to scale horizontally across an ever-increasing number of servers.
```

#### Where to add load balancers

- Between user and web server
- Between web servers and an internal platform layer (application servers, cache servers)
- Between internal platform layer and database

#### Algorithms Used

- Least connection
- Least response time
- Least bandwidth
- Round robin
- Weighted round robin
- IP hash

#### Ways to Implement
- Smart Clients -> database (cache, service, etc) client
- Hardware Load Balancers -> Dedicated Hardware load balancer 
- Software Load Balancers -> Nginx