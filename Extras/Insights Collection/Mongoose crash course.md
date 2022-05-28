## Mongoose.js
Mongoose is an ODM (Object Data Modeling) a framework which makes using mongoDB easier.

- ##### Connecting to a mongo DB using mongoose

```js
const monogoose =  require('mongoose')

mongoose.connect("DB_URL", () => {
  console.log("Connection successful"), (err) => console.log(err);
});
```

- ##### Schema
	- is a configuration object for a model
	- ##### Creating a schema with simple validations
```js
const userSchema = new mongoose.Schema({
	// obj : type
	name: {
		type: String,
		required: true
	},
	email:{
		type: String,
		required: true, // simple validation
		lowercase: true, // will convert the input to lowercase
		minlength: 100
	},
	createdAt:{
		type: Date,
		immutable: true // Once created no change will be allowed for this data value
	},
	hobbies: [String], // accepts an array of values
	address: addressSchema,
	bestFriends: {
		type: mongoose.SchemaTypes.ObjectId,
		ref: "Model"
	}
})

module.exports = mongoose.Schema("User", userSchema)
```

- ##### referencing one schema inside another 
```js
const addressSchema = new mongoose.Schema({
	address: String,
	city: String
})
```

- ##### Mongoose ODMs way arround joins
	- Since joins are costly in MongoDB
	- **populate keyword is used** 
	- Populate lets you reference documents in other collections
	- [populate keyword link](https://mongoosejs.com/docs/populate.html#populate_an_existing_mongoose_document)
```js
const user = await User.where('obj').equals('Value')
user[0].bestFriend("OBJECT_ID_OF_BESTFRIEND")
// save the ref
user.save()
// populate the 
user.populate(bestFriend)

user.save()
```
- ##### Defining custom methods
```js
userSchema.methods.<MethodName> = function(){
	return this.WHAT_TO_RETURN
}
userSchema.methods.sayHi = function(){
	return `Hi, ${this.name}`
}
```
- ##### Middlewares
	- pre
		- `userSchema.pre('save', function(next){ this.updatedAt = Date.now(); next()}`
	- post
		- `userSchema.post('save', function(doc, next){ doc.sayHi(); next()}`