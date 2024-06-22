- JWTs (JSON Web Tokens) are primarily used for verifying user identity in authentication, not for authorization.
- JWTs consist of a Header, Payload, and Signature, allowing for decentralized verification using JWKs (JSON Web Keys).
- OAuth, which uses JWTs, is the de facto standard for authentication, involving multiple types of tokens like ID and access tokens.
- JWTs should be used for verification and as a source of truth for user identity and profile.
- JWTs are static in nature, making them unsuitable for dynamic authorization models like Role-Based Access Control (RBAC).
- JWTs have a size limit, making it difficult to store enough data for complex authorization models like Attribute-Based Access Control (ABAC) and Relationship-Based Access Control (ReBAC)



- Caching is a mechanism to temporarily store data on the client or server side to improve performance.
- Client-side caching involves storing data on the user's device, while server-side caching intercepts requests and returns stored responses.
- Cache hit ratio is crucial to determine the efficiency of caching, defined as the number of successful cache hits divided by total cache requests.
- Caching can reduce server load, especially for read-intensive data endpoints, and is offered by various software implementations like Redis, Memcached, and Varnish.
- Cache key generation should avoid unnecessary parameters to prevent different data for the same endpoint.
- Cache servers can be used as API rate limiters, controlling the number of requests per second and implementing exponential backoff policy for API requests.



### Golang

- Go uses Tricolor mark-and-sweep algorithm for the purpose of garbage collection, It can work concurrently with the program and uses a _write barrier_.
- The primary principle behind this algorithm is that it divides the objects of the heap into three different sets according to their color
```ad-info
In the tricolor mark-and-sweep algorithm:
	- **Black Set**: These objects are fully explored. They have no pointers to the White set and can't be garbage collected.
	- **White Set**: These objects have not been explored yet. They could have pointers to the Black set, but that's okay because it doesn't affect garbage collection. They are candidates for garbage collection.
	- **Grey Set**: These objects are being explored. They might have pointers to the White set.


```ad-summary
The algorithm works by first marking all objects in the Grey set. Then it explores those objects, moving them to the Black set and marking any objects they point to as Grey. This process continues until the Grey set is empty, at which point all reachable objects are in the Black set and all unreachable objects (which can be garbage collected) are in the White set.

If an object in grey set becomes unreachable at some point in a grabage collection cycle, it will be checked and collected in the next cycle

```

- Tricolor Mark and Sweep Algorithm suspends the execution of the program while it is running, which means that it adds latency to the actual process, go tries to handle this by running it as a concurrent process.

#### Go slices
```go
type aStructure struct {
	person string
	height int
	weight int
}

func main() {

	// make a slice ->
	mySlice := make([]aStructure, 0)
	fmt.Println(mySlice)
	newStructs := []aStructure{
		{"Mihalis", 180, 90},
		{"Bill", 134, 45},
		{"Marietta", 155, 45},
		{"Epifanios", 144, 50},
		{"Athina", 134, 40},
	}
	mySlice = append(append(mySlice, aStructure{"Ashwin", 187, 100}), newStructs...)
	fmt.Println(mySlice)
	for _, val := range mySlice {
		fmt.Println(val.person)
	}
}
```


#### Go Pointers #GOPointers

- **Use Pointers**:
    - When you need to modify the original variable.
    - To avoid copying large structures.
    - When you need to maintain shared state.
- **Avoid Pointers**:
    - When the data is small and immutable.
    - When simplicity and safety are priorities.
    - When dealing with concurrency, unless properly synchronized.


In a monorepo-based microservices project with Kubernetes for autoscaling, managing the database can be a challenge as the number of instances increases. Here's a general approach:

1. **Database Replication**: You can use database replication where a secondary database node replicates the data from the primary node. This can handle read operations from the increased number of instances.

2. **Sharding**: To handle write operations, you can use sharding. It's a method of splitting and storing data across multiple databases to improve write performance and scalability.

3. **Database as a Service (DBaaS)**: Consider using a managed DBaaS like Amazon RDS or Google Cloud SQL. They can handle scaling and management of the database for you.

4. **StatefulSets in Kubernetes**: For Kubernetes, you can use StatefulSets which maintain a sticky identity for each of their Pods. This is useful when a Pod needs to be replaced, as the new Pod will inherit the identity and state of the old Pod.

	Remember, the specifics can vary based on the database technology you're using. Always refer to the best practices and guidelines provided by the database vendor.



- Encryption is the process of scrambling data to protect information, with two main types: symmetrical (single key for encryption/decryption) and asymmetrical (using a secure private key and a public key for encryption/decryption).
- Signing files ensures data integrity, proving that the information is accurate and unaltered; an example is signing Git commits to verify the sender's identity.
- Keeping private keys secret is crucial, and maintaining multiple private-public key pairs helps minimize damage if a private key is compromised.
- Encrypting files with the receiver's public key ensures data confidentiality, as the file can only be decrypted by the associated private key.
- Combining encryption and signing ensures both data confidentiality and integrity, protecting sensitive files over the internet.
- It's essential to follow security best practices and continuously learn about new techniques to maintain data security.