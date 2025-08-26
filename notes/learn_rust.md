# contents:

### Ownership

### References

### Lifetimes

### RUST: special rule to leep us safe

# Ownership:

## 3 Rules of Ownership:

- Each value has a owner
- only one owner
- values gets dropped, if its owner goes out of scope

## References:

- takes a reference of a variale and use it to pass to other functions
- once the function completes, the reference is destroyed
- References default to immutable, even if the value referenced to be mutable.
- BUT if we use a mutable reference to a mutable value, then we can use the referecne to change the value as well.
-

```rust
let mut s1 = String::from("akbarsha");
do_stuff(mut &s1);

fn do_stuff(s: mut &String) {
    s.insert_str(0, "Hi, ");
    // (*s).insert_str(0, "Hi, "); // manually dereference
}
```

- we are using the dot operator: to access the string methods on a mutable reference as we do for the value itself
- The dot operator for a method or field auto-dereferences down to the actual value
- so when we are working with dot operator, we dont worry if it is a value or a referecen or even a referenc to a reference.
- if we manually derefereced s, it would look like this: you use an asterisk immediately before a reference to dereference to the value

- x -> variable
- &x - immutable ref.
- &mut x -> mutable ref.
- i32 - type
- &i32 - immutable ref. type
- &mut i32 - mutable ref. type

### Lifetimes:

- Lifetimes can be summed up as a rule that references must always be valid, which means the compiler won't let you create a reference to outlives the data it is ultimately referencing, and you can never point to null.

### RUST: special rule to leep us safe:

- At a give time,
- you can have either Exactly one mutable ref.
- OR
- ANy no. of immutable ref.
