#monolith
#### Monolith Architecture
A monolith architecture is designed as a software where cohesion between services is high. It was created by waterfall methodology. and can be represented as below
![[Monolith Architecture.png]]

#### Microservice Architecture
A microservice architecture is based on the SOLID principles, A single service should perform only one task and do it well, one microservice will not reach into other microservice's DB.
![[Microservice Architecture.png]]

The services have low cohesion, interacting between services is usually done with message queries (ex- RabbitMQ, or Apache Kafaka).
Using this method the services are able to be independent and yet be able to share information in between eachother.

The internal messaging in Microservices, allows individual microservices to consume information when it is able to, leading to asynchronous updates.

By this method DB calls are reduced, as it updates information in bulk rather than for every update.

##### Problems with Microservice Approach
1. **Too many small Databases**.
2. Backup Procedures can be missed.
3. Databases can left unsecure.


#### What is actually being done in microservice approach
Usually, Microservice approach helps in releasing code faster but the database provisioning is a very important task in itself to do so most of the time when designing software for Business groups, this approach is seen.
![[What actually happens.png]]

This very wrong by definition but it works.


