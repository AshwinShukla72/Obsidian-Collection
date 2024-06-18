### Implications
	
- Users Register
- Users Log in
- Users Logout

HTTP is stateless *it means that each request from a client to a server is processed independently*, without any knowledge of previous requests. The server doesn't save information about the client's state between requests. This design helps simplify the server's operations but can require additional techniques, like cookies or sessions, to maintain state when needed.

The idea of an authentication system is make HTTP statefull

- Session Token Storage:
	- 