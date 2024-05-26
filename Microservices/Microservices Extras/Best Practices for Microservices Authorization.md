#microservices

Most authorization is usually handled using gateway, this can actually not be friendly for the platform's performance(_every request must be authorized and authenticated before it is allowed_). If a users request spans through multiple services, for each service the process of authorization and authentication will add significantly to latency.

##### Methods-
1. Enforce JWT(JSON Web Token) Validation 
2. Use RBAC and ABAC to Control End-User Actions 
3. Use Sidecar Enforcement for Security, Performance and Availabilty.
  ![[SideCarMain.png]]
