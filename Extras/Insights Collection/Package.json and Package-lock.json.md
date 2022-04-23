# Why package.json is not Enough?
#nodejs

##### Versioning
**Major.Minor.Patch**

```json
"dependencies":{
	"express": "^4.17.3" // Keep the major version keep other things updated
	"express": "~4.17.3" // Don't touch the minor version keep others updated
}
```

##### What is Package-Lock.json

==**Keeps track of what was actually installed at the beginning of the project**== and keeps track of versioning by getting information from package.json, when `package.json` is changed `package-lock.json` is outdated and is upadated with `npm i`

##### Difference between `npm i`  and  `npm ci`
- `npm i` will  install the best package and  will update the `package-lock.json` file.
-  `npm ci`  ci for  `clean-install` whe n `node_modules` file is not present, if present it will remove it automatically.
- It will never write to `package.json` or any of the package-locks: installs are essentially frozen
-  `npm ci` can only install entire projects at a time: individual dependencies cannot be added with this command.