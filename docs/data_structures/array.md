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

### Reduce

Reduction usage can be complicated but hopefully we can simplify it a bit.
One note is that `reduce` and `fold` are different and we'll highlight this difference below:

```ts title="Reduce"
arr = [1, 2, 3]

arr.reduce((state, value) => state + value)
/* Where state :: Num, the total value so far. It is the first element on the first iteration
 * value :: Num, the next element that is being used
 */
```

This is different to the `fold` function that you see in something like `Haskell`.

Pyes follows a more `Scala`-like approach where it is like reduce, but takes an initial state.
This means that the return type can be different

```scala
arr = [1, 2, 3]

str = arr.fold("")((state, value) => state ++ $"{value}")
// str == "123"
```

Here the `fold` function is curried and so returns another function.

I am yet to decide if I like this approach more than just:

```ts
arr.fold(0, (state, value) => state + value)
// OR
arr.fold((state, value) => state + value, 0)
```

Apparently doing it the curried way helps with type inference though.

#### Right Reduce

Anyone who is familiar with fold, also will know of `foldr` as an alternative.

Typically fold (`foldl`) will apply the function from left to right in the array
However `foldr` applies it from right to left.

There can be many reasons you want to do this, but just for clarity sake, the signature is the same.

## Concatenation

Combining arrays can be done in more than one way, depending on preferred style:

```haskell title="Combining arrays"
arr = [1, 2] ++ [3, 4]

arr2 = [1, 2].concat([3, 4])

-- arr == arr2 == [1, 2, 3, 4]
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

## Array type signatures

```haskell title="Type Signatures"
-- initialisation
arr<A> :: [A]

arr.map<A, B> :: (A => B) => B

arr.filter<A> :: (A => Bool) => A

arr.reduce<A> :: ((A, A) => A) => A
arr.reduceR<A> :: ...

arr.fold<A, B>:: B => ((B, A) => B) => B
arr.fold<A, B>:: (B, (B, A) => B) => B
arr.fold<A, B>:: ((B, A) => B, B) => B
arr.foldr<A, B> :: ...
```
