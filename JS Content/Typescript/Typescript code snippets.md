##### Using multiple types 
```TS
export const removeDuplicates = (

  arr: (string | number)[],

): (string | number)[] => [...new Set(arr)];
```

##### Using Generics ==>
1. Using generics allows array to accept any type of input, ==this in turn allows TypeScript that the function will work with a type that will be specified later==
```TS 
export const removeDuplicatesV2 = <T>(arr: T[]): T[] => [...new Set(arr)];
```
2. Other method

```TS
export const removeDuplicatesV3 = <T extends string |number>(arr: T[]): T[] => [...new Set(arr)]
```


