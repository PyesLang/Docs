# No, but actually why

So you may be thinking, "isn't something like Haskell pretty suited to this already?".
And I could see where you are coming from, but there are many inspirations for Pyes and `Haskell` just doesn't cut it.

## Why not Haskell

### Reason

`Haskell` is an incredible language to learn functional programming in and will make any developer better for learning it.
However, it is still stuck in this academic-oriented mindset that creates a lot of safety, but not as much practicality.
The team slowly is trying to make it more accessible and usable for a wide variety of applications but it's a very slow process.

Doing simple things like writing imperative code, having HashMaps and dealing with IO is just a lot of effort (and ugly syntax).
Now it has it's place, but it isn't in mainstream programming.

### TLDR

Pros:

- Makes better developers
- Helps ensure safer code
- Powerful functional paradigms
- Strong type system for correctness
- Can almost write proofs in the language

Cons:

- Dealing with Monads is a pain for simple tasks
- Data structures become increasingly complicated to manage
- Syntax can become hard to read and understand
- Steep learning curve

### Extra Resources

[Simon Peyton-Jones: Escape from the ivory tower](https://www.youtube.com/watch?v=re96UgMk6GQ)

[Simon Peyton Jones - Haskell is useless](https://www.youtube.com/watch?v=iSmkqocn0oQ)

[What is a Monad? - Computerphile](https://www.youtube.com/watch?v=t1e8gqXLbsU&t=934s)

[Haskell in 100 Seconds](https://www.youtube.com/watch?v=Qa8IfEeBJqk)

## Why not Rust

### Reason

`Rust` is a systems language that has made great strides to take a lot of what makes `C`-like languages great, and make them better with some `Haskell`-like concepts.
It has even made good strides in memory management with the borrow-checker, a fantastic design choice.
It even has a type-system that is really loved as well.
And inherently having a Result type instead of throwing an exception is really fantastic to see.

But alas, all good things come to an end and `Rust` is no exception.
Manual memory management of any kind is realistically over-complicated for the vast majority of use-cases.
And the borrow checker (and references) add extra syntax and reasoning that arguably makes harder to understand code.

Now `Rust` 100% has its place in applications where this extra management is either needed or doesn't bother the users.
But for the majority of modern applications, it just adds a steep learning curve where.

### TLDR

Pros:

- *Blazingly fast*
- Borrow checker help make safer applications
- Strong type system
- Modern tooling (e.g. Cargo)
- Great support and wide community
- Good exception handling

Cons:

- Still requires manual memory management
- Managing references and borrowing can clutter syntax
- Steep learning curve
- Implicit returns :face_vomiting:

### Extra Resources

[Rust's most important containers](https://www.youtube.com/watch?v=f82wn-1DPas)
[Rust in 100 Seconds](https://www.youtube.com/watch?v=5C_HPTJg5ek)

## Python

### Reason

Gosh where to start.

`Python` has its place in this world due to its simplicity and its great interoperability with other languages like `C`.
This allowed developers to write the actual logic in other languages and then expose the simple part of it to `Python`.

Now this is really useful for Data Scientists creating 5-line ML models, but it also adds slow-down for when you're using the actual language.
This isn't usually a problem for most people's applications, but it's something that doesn't sit right with me.

`Python` also lacks proper basic type support, and absolutely lacks anything fun enough to do some cool type-shenanigans.
In all seriousness though, lack of types is just asking to have bugs in your language and it still not having proper support is troubling.

### TLDR

Pros:

- Simple syntax
- Super easy to learn
- Great libraries for doing almost anything

Cons:

- No proper type support (MyPy doesn't count - fite me)
- Syntax is *too* simple for general-purpose IMO
- Slow when having to write actual `Python` code

### Extra Resources

[mCoding](https://www.youtube.com/c/mCodingWithJamesMurphy)
[Python in 100 Seconds](https://www.youtube.com/watch?v=x7X9w_GIm1s)

## TypeScript

### Reason

Gosh am I a `TypeScript` fanboy.
I think it beautifully leverages `JS` in a way that doesn't make you want to die, and has gorgeously powerful type support.
It's truly crazy what you can do with just the type system alone.

However, it still is built on the back of `JS` and with that, come some quirks.
It's `const` values essentially means nothing when it comes to objects and arrays and Object.prototype leaves much to be desired...

### TLDR

Pros:

- Wonderfully expressive types
- Makes `JS` actually usable and makes it enjoyable to write in

Cons:

- Still `JS` under-the-hood
- Limited by creators wanting to be a super-set of `JS` and not a better language
- Slow to transpile and run

### Extra Resources

[Wordle, but types only](https://www.youtube.com/watch?v=JT30j4nhej4)
[Type Challenges](https://github.com/type-challenges/type-challenges)
[TypeScript in 100 Seconds](https://www.youtube.com/watch?v=zQnBQ4tB3ZA)
