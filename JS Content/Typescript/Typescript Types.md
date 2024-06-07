## Any

You can use type `any` as an **escape hatch** when you don’t want something to cause type checking errors

Type `any` represents **all** possible values

You get **no type checking**, so avoid using it
```ts
	const apiResponse: any = {
	  data: []
	}
	// we don't get any warning 😱
	apiResponse.doesntExist
```

Using type `any` is useful in situations where:

You’re working with a library that **lacks** types

You have a **complex API** response you don’t want to type

The API of the code you’re writing **could change**

If you want to focus on writing code 
I suggest instead of using `any` everywhere to include `// @ts-nocheck` at the top of your file. After you’re done writing code turn **type checking** back on.




## Never

Type `never` represents values that **never occur**:

- Type `never` **can’t** have a value
- You use type `never` when there’s **no reachable end point** like a while loop or error exception

```TS
function getPokemonByType(
  pokemonType: 'fire' | 'water' | 'electric'
) {
  // type is 'fire' | 'water' | 'electric'
  if (pokemonType === 'fire') {
    return '🔥 Fire Pokemon'
  }

  // we narrow it down to 'water' | 'electric'
  if (pokemonType === 'water') {
    return '🌀 Water Pokemon'
  }

  // only 'electric' is left
  pokemonType

  // remainingPokemonTypes can't have any value
  // because pokemonType is 'electric' 🚫
  const remainingPokemonTypes: never = pokemonType

  return remainingPokemonTypes
}

getPokemonByType('electric')

```
## Unknown
Type `unknown` is the **type-safe** version of `any`:

- You can assign **any** value to type `unknown` but **you can’t do whatever you want**
- You must use **checks** to **type narrow** a value before you can use a it
- You **can’t access any object properties** unless you **type narrow** first and then use **type assertion**
- Type `unknown` can only be assigned to type `unknown` and type `any`
  ```ts
  const apiResponse: unknown = {data: []}

// assignable to `any` ✅
const anyType: any = apiResponse

// assignable to `unknown` ✅
const unknownType: unknown = apiResponse

// 'unknown' not assignable to type '{ data: []; }'. 🚫
const otherType: { data: [] } = apiResponse

// we have to use checks to narrow down the type
if (apiResponse && typeof apiResponse === 'object') {
  const response = apiResponse as { data: [] }
  response.data // no warning ✅
}
```




## Void
Type `void` is the **absence of having any type**.

There’s no point assigning `void` to a variable since only type `undefined` is assignable to type `void`.

```ts
let pokemon: void

// only `undefined` is assignable to `void` ✅
pokemon = undefined

// Type 'string' is not assignable to type 'void'. 🚫
pokemon = 'Pikachu'
```

Using the return type `void` **explicity** can save us from returning a value on accident during refactor.
```ts
function logPokemon(pokemonList: string[]): void {
  pokemonList.forEach(pokemon => {
    // ...
    return pokemon
  })
}

function logPokemonRefactor(pokemonList: string[]): void {
  for (const pokemon of pokemonList) {
    // ...
    // Type 'string' is not assignable to type 'void'. 🚫
    return pokemon
  }
}

```