# Core Concepts

Pyes is built on some core concepts:

- Immutability
- Purity
- Simplicity
- Strong type inference (Imma try Hilner-Mindley, we'll see)
- First-class functions
- No GC and no manual memory management
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
