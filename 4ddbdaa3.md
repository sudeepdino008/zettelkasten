---
date: 2021-05-13T17:14
---

# Rust: Structs


- **field init shorthand syntax**: when the parameter have the same name as the variables, you can skip the parameter name

```rust
fn build_user(email: String, username: String) -> User {
    User {
        email,
        username,
        active: true,
        sign_in_count: 1,
    }
}
```

- **struct update syntax**: when a new struct instance uses most of the values from an old struct, while just providing new values for a few fields.

```rust
struct User {
    username: String,
    email: String,
    sign_in_count: u64,
    active: bool,
}

fn main() {
    let user1 = User {
        email: String::from("someone@example.com"),
        username: String::from("someusername123"),
        active: true,
        sign_in_count: 1,
    };

    let user2 = User {
        email: String::from("another@example.com"),
        username: String::from("anotherusername567"),
        active: user1.active,
        sign_in_count: user1.sign_in_count,
    };
}


```

the user2 init can be replaced by:

```rust
let user2 = User {
    email: String::from("another@example.com"),
    username: String::from("anotherusername567"),
    ..user1
};
```


- **tuple structs**
No field name. Useful when you actually want a tuple, but also want to name the type. You can also use this when two tuple structure is same, but you need to distinguish the two types. Another reason to use this is if the field names are really redundant (like Color has 3 fields- r, g, b; no need to mention it explicitly)
```rust
struct WriteMessage(String); // tuple struct
struct ChangeColorMessage(i32, i32, i32); // tuple struct
```


- **unit like structs**
these are structs that don't have any fields. 
It's useful when you want to implement some trait on it, but the type itself is empty

- ownership of struct data
You'd usually want the fields ownership to belong to the struct instance. Using something like string slices mean that the ownership belongs somewhere else. So that's something to think about.


- methods vs functions:
  - methods are defined within the context of a struct, enum or trait object.
  - you can define methods for structs using impl. It can take `&self` as parameter to be associated with an instance of the struct. Or it can not take &self as input which makes it an associated function (for example `String::from("blah")`.
  - the parameter taken by a method can be `&self` or `&mut self` or `self`, depending on how you want the ownership to be handled. For example, if the function changes the struct, `&mut self` has to be specified. `self` is used rarely - for example, when you want a transform the instance into something else and the old instance should not be accessible.
  - multiple `impl` blocks can be written (kinda like swift extensions)

```rust

#[derive(Debug)]
struct Rectangle {
    height: u32,
    width: u32
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.height * self.width
    }

    // associated function
    fn square(side: u32) -> Rectangle {
        Rectangle {
            height: side,
            width: side
        }
    }
}

fn rect_area() {
    let square = Rectangle::square(20);

    println!("the area of {:?} is {}", square, square.area());
}

```
