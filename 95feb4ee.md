---
date: 2021-05-26T10:33
---

# Type Systems

categories taken from [wikipedia](https://en.wikipedia.org/wiki/Nominal_type_system)  


## Major categories:

### Nominal vs. Structural

in Nominal type systems the compatibility and equivalence of data types are determined by explicit declarations and/or the name of types. For example, Java have primarily nominal type system:

```java
class Foo {
  method(input: string): number { ... }
}
class Bar {
  method(input: string): number { ... }
}
let foo: Foo = new Bar(); // ERROR!!
```

By contrast, in  structural type systems the compatibility and equivalence is determined by the type's actual structure or definitions and not by characteristics such as name or place of declaration. E.g. Haskell has primarily structural type systems:

```haskell
class Foo {
  method(input: string): number { ... }
}
class Bar {
  method(input: string): number { ... }
}
let foo: Foo = new Bar(); // Okay.
```

Nominal and Structural types might be both present in a type system. For example, Rust has nominal type system for traits (??), but for tuples it follows structural types.
