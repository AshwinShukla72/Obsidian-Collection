```ad-note

- The SOLID principles are a set of object-oriented programming guidelines to improve code quality and maintainability.
	1. The Single Responsibility Principle suggests that a class should have only one reason to change, reducing the likelihood of introducing bugs.
	2. The Open/Closed Principle states that code should be open to extension but closed to modification, promoting code reusability and reducing unintended consequences.
	3. The Liskov Substitution Principle requires that a child class should be able to replace its parent class without affecting the correctness of the program.
	4. The Interface Segregation Principle suggests that classes should not be forced to implement interfaces they do not use, enhancing code flexibility and readability.
	5. The Dependency Inversion Principle recommends that high-level modules should depend on abstractions, not on low-level modules, promoting loose coupling and maintainability.
```

### Single Responsibility principle

> Should do only one thing

The Single Responsibility Principle suggests that a class should have only one reason to change, reducing the likelihood of introducing bugs.
*Example Code:*
```JS
// Ignoring the OOP concepts
// Works but not the best method❌
export const getUserProfilePhoto = async (req, res) => {
	const { token } = req.headers 
	let { email } = req.body
	let isValid = await jwt.verify(token)
	if (isValid) {
		// Get User Data 
		let user = await User.findOne({ email })
		if (user)
	}
	return res.status(401).json({ error: true, message:  "Invalid User" })
}

// As per the above case user should have been validated 
// before reaching the API ✔️
export const validateUser = (req, res,next) => {
	const { token } = req.headers
	const valid = await jwt.verify(token)
	if (valid) {
		next()
	}
	return res.status(401).json({ error: true, message:  "Invalid User" })
}

export const getUserData = (req, res, next) => {
	const { email } = req.body
	const user = await User.findOne({email})
	if (!user) return res.status(404).json({ error: true, message: "User not found"})
	next()
}

// Then the API route would look something like
route.get("/get-user-profile-photo", validateUser, getUserData, getUserProfilePhoto)
```

### Open/Closed Principle:
> functions/Classes should be Open for extension, but closed for modification

The Open/Closed Principle states that code should be open to extension but closed to modification, promoting code reusability and reducing unintended consequences.

```JS
const ROLES = ["user", "admin"]
export const checkRole = (user) => user.role && ROLES.includes(user.role) ?
	  true : false
checkRole({role: "admin"}) //✔️
checkRole({role: "author"}) //❌
// Extending the ROLES array but keeping it the same, as it will extended rather than modified
addRole("author")
checkRole({role: "author"}) //✔️

// USING CLASSES

class Circle {
	constructor(radius) {
		this.radius = radius
	 }
	 area(){
		 return Math.PI * this.radius**2
	 }
}

class Square {
	constructor(length) {
		this.length = length
	}
	area() {
		return this.length**2
	}
}
class CalculateArea {
	static calculate(shape) {
		return shape.area()
	}
}

let circle = new Circle(7)
let square = new Square(16)

console.log(CalculateArea.calucate(circle))

```

### The Liskov Substitution Principle
> The parent class's method can be fully used by the child class

The Liskov Substitution Principle requires that a child class should be able to replace its parent class without affecting the correctness of the program.

```JS
class Bird {
	haveFethears() {
	 // A bird should have feathers
	}
	haveABeak() {
	 // A bird shoudl have a beek
	}
}

class flightlessBirds extends Bird {
	run() {
		// Flightless birds can walk but some some can run
	}
}

class Ostrich extends flightlessBirds {
	
}
```

### Interface Segregation Principle

> A class should not be forced to implement the interfaces it does not use

The Interface Segregation Principle suggests that classes should not be forced to implement interfaces they do not use, enhancing code flexibility and readability.
```JS
class Menu {
	constructor(type) {
		this.type = type
		this.options = type.options
		this.setupOptions()
	}
	setupOptions() {
		this.options.presentMainMenu()
		if (this.options.presentDrinksMenu) {
			// Show the client drinks menu
		}
		if (this.options.presentSweetsMenu) {
			// Show the client sweets menu
		}
	}
	
}
```

### Dependency Inversion Principle

The Dependency Inversion Principle recommends that high-level modules should depend on abstractions, not on low-level modules, promoting loose coupling and maintainability.

```JS
class InventoryTracker {
	constructor(items, requester) {
		this.items = items
		this.requester = requester
	}
	requestItems() {
		this.items.forEach(item => this.requester.requestItem(item))
	}
}

class InventoryRequesterV1 {
	constructor() {
		this.REQUEST_METHOD = ["HTTPS"]
	} 
	requestItem(item) {
		// ...item
	}
}

class InventoryRequesterV2 {
	constructor() {
		this.REQUEST_METHOD = ["RPC"]
	} 
	requestItem(item) {
		// ...item
	}
}

const inventoryTracker = new InventoryTracker(["laptops", "keyboards"], new InventoryRequesterV1())
inventoryTracker.requestItems()
```