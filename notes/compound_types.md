# Compound Types:

- gather multiple values of other types into one type

## Total type: 4

### 4 scalar types:

- Tuple
- Array
- Vector

### Tuple:

- store multiple values of any type
- maximun arity - max 12, but more than 12 we can use with limited functionality

```rust
    let info: (u8, f64, i32) = (1, 3.3, 999); // arity of 4 in this tuple
    let jets = info.0;
    let fuel = info.1;
    let ammo = info.2;

    // else

    let (jets, fuel, ammo) = info;
```

### Array:

```rust
    let buf = [0, 1, 2];
    // else
    let buf = [0; 3] // [value, how many u want]
```

- type annotations for an array:

```rust
    let buf: [i32; 3] = [1, 2, 3];
    let mess = ([3, 2], 3.14, [(false, -3), (true, -100)], 5, "candy");
    mess.2[1].0 // -> true
```

- array live on stack by default
- are fixed by size
- arrays are limited to size of 32

### Vector:

- Vector
- or slices of vector
