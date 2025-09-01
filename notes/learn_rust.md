# contents:

### Ownership

### References

### Lifetimes

### RUST: special rule to leep us safe

### Structs

### Traits

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

### Structs:

```rust
struct RdFox {
    enemy: bool,
    life: u8,
}

let fox = RedFox {
    enemy; true,
    life: 10,
}

// implementation block
impl RedFox {
    // associated func. - they are ofent used as constructors
    fn new() -> Self {
        Self {
            enemy: true,
            life: 10,
        }
    }
}

let fox = RedFox::new(); // using scope (::) operator to access an associated funciton of a struct

let life_left = fox.life;
fox.enemy = false;
fox.some_method();

// methods can be accessed once we initiate the strcut, can be accessed by the dot (.) operator
// the methods can be initialized inside the impl block

impl RedFox {
    // associated fn.
    fn functio_name()
    // methods
    fn move(self) ...
    fn borrow(&self) ...
    fn mut_borrow(&mut self) ...
}


```

#### Scope operator:

- ::
- use it to access parts of namepace-like things
- used in use statements to access items inside of modules
- used to access an associated funciton of a struct

### Traits:

- similar to interfaces in other langiages
- Rust takes the composition over inhritance approach
- Traits define required behaviour
- IN other words, the functions and methods that a struct must implement if it wants to have that trait

```rust
triat Noisy {
    fn get_noise(&self) -> &str
}

impl Noisy for RedFox {
    fn get_noise(& self) -> &str { "Meow?" }
}
```

- The Noisy trait specifies that the truct must have a method name 'get_noise' that returns a borrowed string slice
- so once we have TRAIT involved, we can start writing generic functions that accepts any value that implements that trait

- create GENERIC FUNCTIONS based on traits

```rust
fn print_noise<T: Noisy>(item: T) {
    println!("{}", item.get_noise());
}

impl Noisy for u8 {
    fn get_noise(&self) -> &str { "BYTE!" }
}

fn main () {
    print_noise(5_u8); // prints "BYTE!"
}
```

- COPY type
- TRAITS implement INHERITANCE, so a triat can inherit from another trait

Movement:-
|-- Run -- Ride
|-- Fly

Damage:-
|-- Explode

- Then the HORSE struct that implements ride and explode struct also has to be imlpment the parent traits: movement, run, damage.

Horse:

-- Movement
-- Run
-- Ride
-- Damage
-- Explode

- making your trait inherit from the parent trait really just means that anyone who implments trait is going to have implment the parent trait as well.
- Traits can also have fault behaviors, so if we design structs and traits carefull enough, we might not have to implment some of the trait

Robot:
-- Run

Ostrich:
-- Run

Soldier:
-- Run

Child:
-- Run

```rust
trait Run {
    fn run(&self) {
        println!("Im running!");
    }
}

struct Robot {}
impl Run for Robot {}

fn main() {
    let robot = Robot {};
    robot.run();
}
```
