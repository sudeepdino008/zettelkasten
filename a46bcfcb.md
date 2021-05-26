---
date: 2021-05-21T12:33
tags: 
  - rust
---

# Rust: Type system

the layout of a type is the size, alignment and offsets of its field. For enums, how the discriminant is laid out and interpreted is also part of the type layout.

## size and alignment
- for types implementing `Sized` trait (known at compile type)


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

## Dynamically Sized types
