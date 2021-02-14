# RUST

```rust
cargo new hello_world
cargo build
cargo build - -release
cargo check
cargo run
cargo doc - - open
cargo clippy (to get warnings about potentially useless code like return and semicolon)
```

### VS Code - Extensions:

1. Rust
2. Better TOML
3. Rust (rls)
4. rustfmt

## Notes

**Difference** between an **immutable variable** and a **const** in rust is that a const can't be assigned a value that will be computed on run time and its convention is that the name is in ALL CAPS

const MAX_POINTS: u32 = 100_000;

### let vs mut

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled.png)

### Data Types:

2 types: **scalar** & **compound**

**SCALAR:**

1. integers (underscores are ignore in integers like 1_000_0 is same as 10000)

    can initialize multiple variables likes so

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%201.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%201.png)

    Writing different types of integers

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%202.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%202.png)

2. floating-point numbers

    valid

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%203.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%203.png)

    ALSO valid: (can suffix type at the end as well with or without underscore, which again are ignored):

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%204.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%204.png)

    can also put underscore with numbers and types

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%205.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%205.png)

3. Booleans
4. characters

**COMPOUND:**

1. The Tuple Type (Currently have arity[i.e. total members in tuple] of 12 after which although you can have more arity but not with full functionality)
The tuple size can't grow or shrink it stays the same (arity of 3)

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%206.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%206.png)

    Destructuring:

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%207.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%207.png)

2. The Array Type `(ARRAYS HAVE MAX LENGTH OF ***32*** IN RUST AFTER WHICH THEY LOSE THEIR MOST FUNCTIONALITIES )`

    Arrays in Rust are different from arrays in some other languages because arrays in Rust have a fixed length, like tuples.

    *Arrays are useful when you want your data allocated on the stack rather than the heap (we will discuss the stack and the heap more in Chapter 4)*

    use array *only*  when you know the number of elements in it won't change etc. (like names of months) else use vector **Vec** 

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%208.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%208.png)

    to initialize an array of same type a specific number of times (so the value 3, 5 times):

    ```rust
    let a = [3; 5];
    ```

    equal to :

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%209.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%209.png)

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2010.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2010.png)

CONST:

SCREAMING SNAKE CASE

TYPE ANNOTATION IS MANDATORY

VALUE SHOULD BE A LITERAL

## Strings:

There are total 6 types of strings in std lib but mostly we use 2:

1. string slice `str` will almost always see it as borrowed string slice `&str` 

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2011.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2011.png)

2. Second is `String` 

    `Capacity` may or may not be fully used
    a `&str` is a subset of `String`

    ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2012.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2012.png)

    Strings can't be indexed by character position so my_string[2] is invalid

    - **THINGS YOU CAN DO IF YOU KINDA WANT TO INDEX THROUGH STRING**

        `word.chars()` gives you an iterator to iterate through unicode scalars

        ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2013.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2013.png)

        ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2014.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2014.png)

        or a library 

        ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2015.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2015.png)

        ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2016.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2016.png)

    - Different methods to manipulate strings

        ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2017.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2017.png)

    you can also use .nth(index) along with an iterator to be able to go to an index

    1. A literal string is always a borrowed string slice `&str` 

        ![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2018.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2018.png)

Difference is that in `&str` data CANNOT be modified and in `String` it CAN be!

need to call a `.to_string()`on borrowed string slice to to convert it to `String`

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2019.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2019.png)

OR

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2020.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2020.png)

## Shadowing

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2021.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2021.png)

THIS is shadowing, meaning in a scope you can shadow a variable, it won't change its value but rather make a copy of it which will "shadow" its original value

value of the first x isn't accessible from the inner block after it is shadowed.

variables can be shadowed for different accessibility like:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2022.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2022.png)

and can also be shadowed to entirely different data type to drop intermediary usage/meaning of a variable in a code like:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2023.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2023.png)

## [**Functions and Expressions are different**](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html#function-bodies-contain-statements-and-expressions)

Expressions never end with ;

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2024.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2024.png)

RUST implicitly returns last expression as return value like: 

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2025.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2025.png)

but see here 5 in five() is an expression which is fine but if we added a ; at the end of it, it would ***become a statement hence won't be able to return any value***

but if we ***add a return before 5;*** then it will be fine and will compile.

## [Flow control:](https://doc.rust-lang.org/book/ch03-05-control-flow.html)

SOME POINTS ABOUT IF:
1. everything between `if` and `{` is a condition
2. Condition must evaluate to condition (RUST hate type coercion)
3. IF is an `expression` which means it returns value

SOME POINTS TO REMEMBER EVEN MORE!!

1. There are no ; after the branch values so values can be returned as tail value
2. we can't use `return` even if we wanted to, because return is for function values
3. all the arms (blocks from if and else) return the same type
4. `;` At the end of the entire IF expression; (IT IS MANDATORY TO PUT IT IF YOU USE THE VALUE, else you can drop it) - but make it a practice to always put ; after if
5: `{}` are mandatory

if:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2026.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2026.png)

you can't just say "if number{}" in rust like you can in JS 

**DON'T use too many if/else instead use match in rust**

instead of ternary use: 

```rust
let number = if condition { 5 } else { 88 }; 
```

this won't work, cause of mismatched types:

```rust
let number = if condition { 5 } else { "six" };
```

## Loops:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2027.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2027.png)

look at the break statement you can return what you want to after the break statement in a code 

**While loop for iterating over array:** 

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2028.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2028.png)

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2029.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2029.png)

there are different types of iters that can work in different ways to return calues

### Ranges in for loops

start inclusive, end exclusive:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2030.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2030.png)

both ends inclusive

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2031.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2031.png)

### Labeling a loop:

you can label a loop in rust for example to break out of the top most loop instead of using other methods to achieve the same purpose;

like so:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2032.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2032.png)

`'bob`

similar stuff for continue:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2033.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2033.png)

## Makeshift switch case:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2034.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2034.png)

## [Ownership in RUST:](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2035.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2035.png)

Not valid: (scope for s ended on line 4)

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2036.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2036.png)

Valid:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2037.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2037.png)

### ONLY 1 OWNER

ownership has been moved from s1 to s2, and now s2 is uninitialized

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2038.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2038.png)

line 1:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2039.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2039.png)

NOT POSSIBLE IN RUST FOR MEMORY SAFETY:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2040.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2040.png)

INSTEAD 

on line 2
s2 exists on stack but is uninitialized now 

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2041.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2041.png)

Since s1 is immutable we can't reassign it to another value and we can't use it anymore. BUT you can still shadow it (but remember rules of shadowing told below)

like this works:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2042.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2042.png)

To make a copy of it, instead of moving just use `s1.clone()`

clone does the following under the hood (copy stuff in stack and heap)

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2043.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2043.png)

RUST reserves the word **COPY** for only when `stack` data is being copied.
For both `stack` **and** `heap` data **CLONE** is used

## Surprise!

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2044.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2044.png)

here the s1 got moved to the do_stuff() function and we can't use it

an approach could be that we make s1 a mut variable and the at the end of the do stuff function return s while moving the call like so `s1 = do_stuff()` but come on that's ehh pattern. so that's why we'd now learn about REFERENCES AND BORROWING

**Similarly: ERROR!!!!**

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2045.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2045.png)

references can't be used to change data of the referenced variables as references are defaulted to immutable BUT you can do that if you use mutable references like so:

**NO ERROR!**

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2046.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2046.png)

# References & Borrowing

using `&` to pass references 

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2047.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2047.png)

under the hood:

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2048.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2048.png)

in rust you almost never have to care about pointers cause it automatically handles creation and destruction of it and make sure they are always valid (using lifetimes) andddd you can never point to null 

Compiler won't let you create a reference that outlive the data it is ultimately references 

References defaults to immutable EVEN IF the value they refer to are immutable

## Dereferencing:

*for calling methods:*

usually when trying to get a value from a **reference** we need to *de reference* it to "get" the actual value, but in rust you can use the `.` operator (it auto deferences dowwnnnn (incase it is a ref of ref of ref ...) to the actual value):

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2049.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2049.png)

*for most other operators (like assignment operator ) you have to manually derefernce it like so:*

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2050.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2050.png)

[What is what](https://www.notion.so/544f2f4e671b4ec79caff52ff71ae74f)

dereferncing to get actual value

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2051.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2051.png)

![RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2052.png](RUST%20c4f463e3251140979dafc776e27aaacb/Untitled%2052.png)

**YOU CAN HAVE Either (for one variable)

1. Exactly one mutable reference
2. Any number of immutable references**

it is to make sure that different mutable references can't change the value of a variable, and cause memory problems, in usual cases this will require some sort of locking but rust saves us from those stuff

## Memory Safety:

Rust guarantees memory safety at compile time

# Structs & Traits:

not sure what to write the [video](https://www.udemy.com/course/ultimate-rust-crash-course/learn/lecture/17981939#overview) explains it flawlessly

# Collections:

#[derive(Debug)] // !This enables using the debugging format string "{:?}"

## Notes (OLD):

- macros usually go with ! mark at end
- **LET** makes immutable variables here
- ALL the variables are by default immutable in rust
  - to make it mutable `let mut b: i8 = 0` "mut" keyword
- `usize` & `isize` are native variables meaning they'll use space of that processor, like 64 unsigned/signed integer respectively
- `rm -rf ~/.cargo/.package-cache`
- `rm -rf ~/.cargo/registry/index/*`

**Formatting Traits:**

```rust
error: unknown format trait `s`
  --> hello.rs:10:22
   |
10 |    println!("{} of {:s} people know binary, the other half doesn't", 1, 2);
   |                      ^
   |
   = note: the only appropriate formatting traits are:
           - ``, which uses the `Display` trait
           - `?`, which uses the `Debug` trait
           - `e`, which uses the `LowerExp` trait
           - `E`, which uses the `UpperExp` trait
           - `o`, which uses the `Octal` trait
           - `p`, which uses the `Pointer` trait
           - `b`, which uses the `Binary` trait
           - `x`, which uses the `LowerHex` trait
           - `X`, which uses the `UpperHex` trait
```

**Implementing Display for custom structures**

```rust
#[derive(Debug)]
struct Complex {
    real: f64,
    imag: f64
}
impl fmt::Display for Complex {
    fn fmt (&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "{} + {}i", self.real, self.imag)
    }
}
```
