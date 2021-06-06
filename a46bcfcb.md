---
date: 2021-05-21T12:33
tags: 
  - rust
---

# Rust: Type system

the layout of a type is the size, alignment and offsets of its field. For enums, how the discriminant is laid out and interpreted is also part of the type layout.

## size and alignment
- for types implementing `Sized` trait (known at compile type). Rust implicitly adds `Sized` to every generic function.


- **alignment** of a value specifies what addresses are valid to store the value at. A value of alignment `n` must only be stored at an address that is a multiple of n. So, a value with alignment 2 must be stored at an even address. 
- alignment is measured in bytes, must atleast be 1, and always have a power of 2.
- use `align_of_val` to find the alignment of a value. All references to a value of specified type must be a multiple of this number.

```rust
use std::mem;

fn main() {
    let val: u32 = 100;
    println!("alignment of u32 is {}", mem::align_of_val(&val));
}
```



- **size** of a value is the offset in bytes between successive elements in an array with that item type including alignment padding.
- This value is always a multiple of its alignment. This might be different from alignment when say, for an array of u64 in a 32-bit platform.
- can be checked by `size_of::<T>()` function.
- `size_of_val::<T>()` can also be used when `T` has no statically known size e.g. a slice `&[T]` or a trait object.

## Dynamically Sized types (DST)
- sizes are known only at runtime.
- `str` (not `&str`) is a DST. 
- Rust doesn't allow to create a variable holding of DST as it might have different sizes at compile time (but Rust needs each type to take the same amount of space).

```rust
// FAIL!!
let s1: str = "Hello there!";
let s2: str = "How's it going?";
```

- so instead we use `&str` which stores the location of string in heap, and the length. In general this is how DSTs are stored - by having a metadata store the size of dynamic information. This is the golden rule of handling DSTs - it has to be put behind pointers of some kind.

- trait objects are a kind of DST, which are behind pointers - `&dyn Trait_Name` or `Box<dyn Trait_Name>` etc.


- `?Sized` it's the opposite of `Sized`. 
```rust
fn generic<T: ?Sized>(t: &T) {
    //
}
```
Here, `T` might or might not be `Sized`. This is only available for `Sized` trait. Also note that the type of t parameter is `&T` since it might be dynamic type and therefore needs to be behind a pointer.

