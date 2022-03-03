

### Summary

He proposes that instead of modularizing a software on the basis of flowchart, they need to be modularised on the basis of the changes that might arise. The two points above ensure every piece of code has a clear purpose and when design changes are in order, half the codebase isn't invalid. When the *properly decomposed domain concepts* are modeled, they don't spread their implementation details all over the codebase (This exhibits the encapsulation). 

### Notes
**David Prarnas** elaborated on the criteria to use when decideing which pieced of code should reside together which ones need to be separate.

He basically says,
- He discussed two different strategies for decomposing and separating the logic in a simple logarith
- On domain level, they are concepts of your problem space
- To certain extent, they are dependent on each other.
- Ex: When you purchase an item, you do not worry about how it is stored. **Modularity**
- Same way, the implementations of these concepts must be separate as well.
- **Encapsulation**, When properly decomposed domain concepts are modeled, they don't spread their implementation details all over the codebase

The two points above ensure every piece of code has a clear purpose and when design changes are in order, half the codebase isn't invalid

>
“We have tried to demonstrate by these examples that it is almost always incorrect to begin the decomposition of a system into modules on the basis of a flowchart. We propose instead that one begins with a list of difficult design decisions or design decisions _which are likely to change_. Each module is then designed to hide such a decision from the others.”
>

