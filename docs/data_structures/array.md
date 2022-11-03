# Arrays

The Pyes version of an array will be familiar in some form to most people, with similar functionality.

An array under the hood is essentially a generic type, being able to be a list of any data-type.

## Initialisation

The type of the array is inferred and so doesn't need to be specified.

```haskell title="Array initialisation"
arr = [1, 2, 3]
```

You aren't able to specify an empty array first and then populate it as that wouldn't be immutable.
However, you can still create an empty array like this just fine:

```haskell title="Empty array"
arr = []
```

## Functional Usage

### Inline arrow functions

These are functions that are passed to functional operations on arrays (and technically others).
This is where the function is inlined so that it does not need to be defined externally

It follows the format `(elem) => elem + 1` or `_ + 1` if the `_` wildcard is used.

The wildcard is only recommended for simple map operations as its usage beyond this would make code unclear.
It is also only usable for inline arrow functions where the value is immediately returned.
It would not be possible in the following example:

```ts
arr = [1, 2, 3]

arr2 = arr.map(elem => {
  x = 1
  return elem + x
})
```

### Map

Simply applies the given function to each element of the array, returning a new array with the results and with the same length:

```ts title="Array map"
arr = [1, 2, 3]

arr2 = arr.map(elem => elem + 1)

// arr2 = [2, 3, 4]
```

You can also use the wildcard `_` for shorthand mapping operations:

```ts title="Map shorthand"
arr = [1, 2, 3]

arr2 = arr.map(_ + 1)
```

### Filter

The usage of the word filter has always baffled me.
It seems like it is ripe for uncertainty as to whether or not the items returned match the condition(s) given.

So instead, Pyes uses the `where` keyword.
You might have seen similar things with LINQ in `C#`.

```ts title="Filtering an array"
arr = [1, 2, 3]

arr2 = arr.where(_ >= 2)

// arr2 = [2, 3]
```

## Type Unions

For union types in arrays, the typing has to be explicit to ensure that the user intended this unholy mash-up:

```haskell title="Unholy"
arr :: [Int | String] = [1, 2, "hello"]
```

Similar can be said for concatenation of 2 different array types:

```haskell title="Unholy Cons"
arr :: [Int | String] = [1, 2] ++ ["hello", "world"]
```

So the following <span style="color:red">wouldn't</span> work:

```haskell title="Invalid Cons"
arr = [1, 2] ++ ["hello", "world"]
```
