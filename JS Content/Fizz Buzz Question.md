
#### Method 1: BAD (looks fancy but actually bad)
Time Complexity is ==O(n^2)== because of two nested methods fill and map
```TS
export const fizzBuzzArrayCreator = (range: number): (number | string)[] =>
	Array(range)
		.fill(0)
		.map((value, index) => index + 1)
		.map((e) => {
			if (e % 3 === 0 && e % 5 === 0) return "FizzBuzz";
			if (e % 3 === 0) return "Fizz";
			if (e % 5 === 0) return "Buzz";

			return e;
		});
```

#### Method 2: Simplest method
==time complexity = O(n)==, where n is the range, because you're iterating through the range once and performing a constant number of operations for each element. The ==space complexity == O(n)==, as you're creating a new array of length n in the worst case (when all numbers are pushed into the array)
```TS
const fizzBuzzArrayV2 = (range: number): FizzBuzz[] => {
	const result : FizzBuzz[] = [];
	for (let i = 1; i <= range; i++) {
		// ---------- easy to tell
		if (i % 3 === 0 && i % 5 === 0) result.push("FizzBuzz");
		else if (i % 3 === 0) result.push("Fizz");
		else if (i % 5 === 0) result.push("Buzz");
		else result.push(i);
		
		// ---------- 
		let word = ""
		if (i % 3 === 0) word += "Fizz";
		if (i % 5 === 0) word += "Buzz";
		result.push(word || i)
	}
	return result as FizzBuzz[];
};

```

#### Method 3: using Maps
Too complex

```TS
export const fizzBuzzArrayV4 = (range: number): FizzBuzz[] => {
  const result: FizzBuzz[] = [];
  const map = new Map<number, string>([
    [3, "Fizz"],
    [5, "Buzz"],
  ]);

  for (let i = 1; i <= range; i++) {
    let word = "";
    map.forEach((val, key) => {
      if (i % key === 0) word += val;
    });
    result.push(word || i);
  }
  return result;
};
```
