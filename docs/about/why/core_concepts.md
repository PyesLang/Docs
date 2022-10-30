# Core Concepts

Pyes is built on some core concepts:

- Immutability
- Purity
- Simplicity
- Strong type inference (Imma try Hilner-Mindley, we'll see)
- First-class functions
- No GC and no manual memory management
- No null/undefined/None
- *Blazingly fast*

## Immutability

### Problem

Most languages (e.g. `Java`, `Python`, `JS`) allow mutability front and centre.

This means that you can't be certain of the state of your code at any given point.
Sometimes, you don't even know the type of the variables you're working with.

I believe (and so do the people at `Haskell`) that this makes code harder to reason about and understand.
When  you variable can't change value, you don't have to worry about some function somewhere updating it due to it's reference being passed around.

Now other languages (e.g. `Rust`) are immutable by default and require explicit annotation to allow otherwise.

This is nice for cope based memory management and for making reasoning easier.
But it's a bit of a cop-out by still allowing developers to make this poorly reasoned code.
And we all know that developers can't think good.

### Solution

Those of you who are familiar with `Haskell` will already see this coming.
To make the reasoning easier, we instead insist that all parts of the language are immutable, not just when users want them to be.

You may be asking to yourself, "how come other languages don't follow this paradigm then?".
And while that is generally true, there have been strides to actually overcome that.
[Anjana Vakil](https://anjana.dev/) has made some great videos on this to explain the benefits and usages of immutable data structures in `JS`:

- [Learning Functional Programming](https://www.youtube.com/watch?v=e-5obm1G_FY)
- [Immutable Data Structures](https://www.youtube.com/watch?v=Wo0qiGPSV-s)

Now she references resources for doing this but quite nicely highlights benefits and limitations of applying immutability to a language that is not natively immutable.
Part of the problem is that `JS` isn't designed to handle this part of the functional programming world and so its usage is still somewhat limited.

I do have one interesting potential caveat for later in these docs (INSERT HERE) that might anger the hardcore purists though...

## Purity

This goes hand-in-hand with immutability in general, so it makes it quite easy to reason about at this point.

Pure functions are when the function only acts on its inputs and isn't reliant on global state for the output of the function.
It also doesn't allow for external state to be modified (which in this case is a no-brainer given immutability).

This encourages (and somewhat enforces) developers to write code where each function is a section of a pipe-line, minimising hard-to-reason-about side-effects.
This helps to minimise bugs in the code and makes doing functional things like mapping over an array, more intuitive.

## Simplicity

Modern languages have tended towards simplicity in various different manners.
However, they can sometimes make quite significant compromises in some cases due to complexity of the language.

Ideally, you shouldn't end up with too much syntax for day-to-day code without sacrificing syntactic power.
Some examples of this might be in how Haskell mainly just has you add type definitions to functions and not much else.
Or languages that allow concise list comprehensions in conjunction with other array methods.

## Type Inference

Have you ever got a bit sick and tired of manually making every type explicit, even when to you it's obvious what the type should be?
That there is evidence that the language has poor type inference.

Some languages (like C#), sacrifice this for low-level performance improvements.
However, in the process of doing this, they are sacrificing developer readability and writability.
It makes writing simple data structures a chore when you have to do something like:

```java
HashMap<string, List<string>> mapping = new HashMap<string, List<string>>([("hi", ["ho"])]);
```

as opposed to writing:

```c#
var mapping = new HashMap<string, List<string>>([("hi", ["ho"])]);
```

or even something like:

```haskell
mapping = new HashMap([("hi", ["ho"])])
```

where the type can be inferred by the input to the constructor.

## Memory Management

Now as much as some very clever people have done a lot of work doing some very clever stuff in this field, I am not on of them.

You may ask, "Why not just build the whole thing on top of the JVM or DotNET?".
Valid question. Moving on from that.

So instead of letting people manually manage their own memory, the goal is to go for compile time memory management.
Where the relevant data is freed at their end of its scope.
Which with immutable data and pure functions, shouldn't be too challenging of a concept (in theory...).

## No null values

The [Billion Dollar Mistake](https://www.youtube.com/watch?v=ybrQvs4x0Ps) is one many of us have probably felt at various points in our programming journey.
It has lead to crashing programs and famously `undefined is not a function` style behaviour in `JS`.

Now some more modern approaches are to have an `Option<T>` type where you have to explicitly handle the `None` possibility.
I do not believe that is a good enough approach.
Instead, all data must contain a value that is not null.

## *Blazingly Fast*

When coming up with simple languages, usually people go for interpreted languages that are slow AF.
Instead, the plan with Pyes is to target LLVM (and whatever Windows uses) and to leverage the already excellent platform there.

An example of this working is none other than `Rust` itself.
