# Rust Learning Notes
**Author: Jarrett Dowling | Date: May 14, 2024**

*Rust Documentation: https://doc.rust-lang.org/stable/book/*

## Style and Base Syntax
- *4 spaces not tabs*
- Uses ";" to end lines and "main" function
- comments use '//'

```funtname!()``` is a *macro* (The "!" means it is a macro not a function).

## Functions
Syntax: 
```fn functname() {}```

eg.
```
fn another_function(x: i32) {
    println!("The value of the arg is: {x}");
}
```
*types are required to be declared in function signatures*

### Return Values
*return values are not named and thier type must be declared using an arrow*
ie.
```
fn five() -> i32 {
    5
}
```
The function 'five()' returns a signed 32-bit int (5) when called.
*Note: return expressions should not have semi-colons.*

## Variables
Syntax:
```
let a = 5;
let mut b = String::new();
```
*This makes two variable, where a is immutible and b is mutable. b is a new empty string.*
*can do ```let a = 'type';``` or for explicit type annotation can do ```let a: 'type' = 'val';```*

### Constants
Syntax:

```const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;```

*This is a 32bit unsigned int with constant value 10800*

### Shadowing
A shadowed variable is a variable in an inner scope named the same as one in an outer scope.
This "overshdows" the variable name to the new variable for the scope. eg.
```
let x = 5;
{
    let x = x + 5;
    println!("Inner scope x is: {x}");
}
println!("Outer scope x is: {x}");
```
which outputs:

*Inner scope x is: 10*

*Outer scope x is: 5*

## Data Types
### Int Types
Integers:

|Length|Signed|Unsigned|
|-----|-----|-----|
|8-bit| i8 | u8 |
|16-bit| i16 | u16 |
|32-bit| i32 | u32 |
|64-bit| i64 | u64 |
|128-bit| i128 | u128 |

*signed used 2's compliment*

Integer Literals:
|Literal|Example|
|-------|-------|
| Dec | 98_222 |
| Hex | 0xff |
| Oct | 0o77 |
| Bin | 0b1111_0000 |
| Byte (u8 only) | b'A' |

### Float Types
*Default is 64-bit*
Uses the same naming conventions as integers but with f in place of u. This gives f32 and f64.

### Numeric Ops
```+``` is addition

```-``` is subtraction

```*``` is multiplication

```/``` is division

```%``` is remainder

### Boolean
Uses the keywords 'true' and 'false'.

```let a: bool = false;```

### Characters
*Char literals use single quotes '' while strings use double quotes ""*

```let c = 'z';```

```let z: char = '😻';```

*Char is a 4-byte unicode value*

#### Compound Types
##### Tuple
A tuple in rust is a comma separated list of values.

```let tup: (i32, f64, u8) = (500, 6.4, 1);```

```tup.0``` is the value 500.

##### Array
Rust arrays are stack allocated rather than heap allocated.

```let a = [1, 2, 3, 4, 5];```

or

```let a: [i32; 5] = [1, 2, 3, 4, 5];```

*the square brackets tell say type is i32 and array contains 5 elements*

```a[0]``` gives the first element in the array.

## I/O
Including the Lib:
```use std::io```

Getting input:

```let mut guess = String::new();```

```
io::stdin()
    .readline(&mut guess)
    .expect("Failed to read line");       
```
*This is passing guess by reference and mut to make it mutable by readline.*

*expect is handling the errors / failures.*

Printing output:

```println!("You guessed: {guess}");```

or

```println!("You guessed: {}", guess);```

## Control Flow
### If Expressions
Like normal
```
if number < 5 {
    println!("True!");
} else {
    println!("Flase");
}
```

### Loops
*The rust keyword 'loop' runs an infinite loop*
Loops can be labeled
```
'counting_up: loop {

}
```
is a loop labeled counting_up and can be broken using ```break 'counting_up;```

#### While
Just like normal.
```
while number != 0 {}
```

#### For
*Can do for element in array like python*
```
for number in (1..4).rev() {
    println!("{number}!");
}
```
gives:
4!
3!
2!
1!

## Ownership
### Base Ownership
**Memory is freed after the variable that "owns" it goes out of scope.**

This is easy for simple data types (ie. ints, floats, bools, etc.) but can be difficult for data types like strings since the pointer and length are copied and not the "data". This can cause double free errors when both strings with the same pointer go out of scope. 
**Rust uses "moves" rather than copy for strings, invalidating the first variable to avoid this issue.** 
To deep copy the variable (copy the var and the pointed to data) rust uses the ```clone()``` method.

For functions, simple data types (ints, bools, floats, etc.) are passed by copy, so the original variable is still in scope, and the called function now has ownership of the copy. Functions in rust pass by "move" when passing non-simple data types (strings and other types with clone method). This means that the called function now "owns" the variable and the original variable is no longer valid.

For Return values, ownership is given to the variable "collecting" the return value.

*Summary: When a variable goes out of scope the value is cleaned by ```drop``` unless ownership is "moved" to another variable that doesn't go out of scope.*

### References and Borrowing
Since changing ownership just to let a function use a variable and then pass it back is tedious, rust lets us use references (ie. pointers but guaranteed to point at valid data of that type).

*"&" represent references and "\*" is the dereference operator*

Creating and using a reference is called "Borrowing". Since the function is only borrowing the variable, it does not own it (no drop is called) and it is immutable (the function cannot modify something it has a reference to). References can be made mutable (to be able to edit the data), but then there cannot be any other references to that data. Pointers can be created after the last use of the previous pointer.

```
let mut s = String::from("Hello");

let r1 = &s; 
let r2 = &s; // no problem since neither are mutable
println!("{} and {}", r1, r2);
\\ r1 and r2 will not be used after this point

let r3 = &mut s; // no problem since after last use of r1 and r2
println!("{}", r3);
```

### Slices
See Docs for easy explination.

## Structs
Defining a struct

```
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}
```

*Inside the struct are the fields*

and using the struct

```fn main() {
    let user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };
}
```

*Dot notation is used to get the data from a struct (ie. ```user1.email```).*

If the struct is mutable, the dot notation is used to change the values as well. *The entire struct must be either mutable or not, rust doesn't allow for only some fields mutable.*

The creation function below uses field-innit shorthand to use the parameters of the function as the corresponding fields of the struct.

```
fn build_user(email: String, username: String) -> User {
    User {
        active: true,
        username,
        email,
        sign_in_count: 1,
    }
}
```

### Methods
Syntax:

```
impl structname {
    fn method1(&self) {
        ...
    }
}
```

*Methods are called using the dot notation as well. (ie. ```struct1.method1()```)*

## Enums
They are data tyoes where there are multiple choices for the same thing. i.e. IP addresses can be put in an enum to get the data type IpAddrKind with two choices, v4 and v6.

```
enum IpAddrKind {
    V4,
    V6,
}

let four = IpAddrKind::V4;
let six = IpAddrKind::V6;
```

Each choice in an enum is called a variant. One advantage of enums is that each variant can be a different type and can directly hold the data. eg.

```
enum IpAddr {
        V4(u8, u8, u8, u8),
        V6(String),
    }

let home = IpAddr::V4(127, 0, 0, 1);
let loopback = IpAddr::V6(String::from("::1"));
```

### Option
The option enum is a standard library enum that encoded a value that is something or nothing. This is to replace the "null feature" that other languages have. (The option enum uses ```<T>``` syntax that is a generic type parameter.) 

```
let some_number = Some(5);
let some_char = Some('e');

let absent_number: Option<i32> = None;
```

### Match
The match control flow construct matches the given enum variant to the code that should be run for it.

```
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter,
}

fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```

The "=>" separates the pattern (variant) to match and the code to be run. Braces are used if multiple lines of code are needed to be run. Match must be exaustive (ie. all possiblilities must be covered.) but you can set a default using the "other" keyword. If we want a catch all but don't want to pass the value on, we use the "_" and if we don't want any code to run, we can use an empty tuple "()".

### If let
The if let syntax lets us combine if and let.

```
let config_max = Some(3u8);
match config_max {
    Some(max) => println!("The maximum is configured to be {}", max),
    _ => (),
}
```

and 

```
let config_max = Some(3u8);
if let Some(max) = config_max {
    println!("The maximum is configured to be {}", max);
}
```

both behave the same way.

## Cargo
*Come back to chapter 7
### Packages and Crates

## Common Collections

### Vectors

There are two ways to make a vector

```let v: Vec<i32> = Vec::new();```

or using the macro and letting the compiler set the type

```let v = vec![1,2,3];```

*Vectors hold a dynamic bunch of the same type*

Adding to a vector uses the push method:

```
let mut v = Vec::new();

v.push(5);
v.push(6);
```

Reading the elements can be done with indexing or with the get method,

```
let v = vec![1, 2, 3, 4, 5];

let third: &i32 = &v[2];

let third: Option<&i32> = v.get(2);
```

Iterating through a vector:

```
let v = vec![100, 32, 57];
for i in &v {
    println!("{i}");
}
```

prints all of the elements in the vector. To change each element you need to make the vec mutable and use ```&mut v``` as the iterator.

Since vectors can take any type, you can use enums as the "type" and store multiple types in the same vector.

*Like other structs, freeing a vector frees all of its elements as well.*

### Strings

*All strings are stored in UTF-8. ```str``` is a string slice and is built into rust, while ```String``` is provided by the std lib.*

Creating a string:

```let mut s = String::new();```

and string literals can be made strings by using

```let s = "Hello World!".to_string(); ```

or 

```let hello = String::from("Hello");```

Updating a String:

```
let mut s = String::from("foo");
let s2 = "foobar"
s.push_str("bar");
s.push_str(s2);
println!("{s}");
```

outputs ""foobarfoobar.

*the push_str method does not take ownership of s2*

We can use the push method to add one char to the String.

Concatination:

We use the ```+``` operator to concatinate Strings.

```
let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2; // note s1 has been moved here and can no longer be used
```

*s1 is no longer valid, since it is moved to s3, while s2 is valid since it was passed by reference. The concatination method adds one string to self, which is why the second string is a reference.*

Concatinating multiple Strings can be difficult to see, so we can also use the format macro.

```
let s1 = String::from("tic");
let s2 = String::from("tac");
let s3 = String::from("toe");

let s = format!("{s1}-{s2}-{s3}");
```

Indexing into Strings is not allowed in rust. I.e.

```
let s1 = String::from("hello");
let h = s1[0];
```

is invalid.

Slicing Strings:

While rust doesn't allow for integer indexing, it does allow slicing.

```
let hello = "Здравствуйте";
let s = &hello[0..4];
```

where ```s``` is a ```&str``` that combines the first 4 bytes of the String. Since each char is 2 bytes, that means ```s``` is Зд. All slices must be in multiples of 2 or rust will panic.

Iterating over Strings:

```
for c in "Зд".chars() {
    println!("{c}");
}
```

Prints:

3
д

### Hash Maps

Creating a new Hash Map:

```
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);
```

*Notice that since hash maps are not used very often, they are not automatically included in the scope.*

Accessing values in a Hash Map:

```
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);

let team_name = String::from("Blue");
let score = scores.get(&team_name).copied().unwrap_or(0);
```

We use the get method, which returns an ```Option<&V>``` that returns ```None``` if there is no value. The copied method is then called to "derefernce" and get the value rather than the reference.
Lastly, the unwrap_or(0) method sets the score to 0 if the hash map has no entry for the key.

Iterating over the whole Hash Map:

```
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);

for (key, value) in &scores {
    println!("{key}: {value}");
}
```

Hash Maps and Ownership:

```
use std::collections::HashMap;

let field_name = String::from("Favorite color");
let field_value = String::from("Blue");

let mut map = HashMap::new();
map.insert(field_name, field_value);
```

*The inserted fields are copied if possible, or they are moved to the Hash Map.*

Updating a Hash Map:

Each unique key can only have one value at a time.

There are three ways to deal with updating the value.

1. Overwriting

```
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Blue"), 25);

println!("{:?}", scores);
```

```{"Blue": 25}```

2. Adding the value only if no value is present

```
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);

scores.entry(String::from("Yellow")).or_insert(50);
scores.entry(String::from("Blue")).or_insert(50);

println!("{:?}", scores);
```

```{"Yellow": 50, "Blue": 10}```

3. Updating the value based on the old value

```
use std::collections::HashMap;

let text = "hello world wonderful world";
let mut map = HashMap::new();

for word in text.split_whitespace() {
    let count = map.entry(word).or_insert(0);
    *count += 1;
}

println!("{:?}", map);
```

```{"world": 2, "hello": 1, "wonderful": 1}```

## Error Handling

### Panic!

The ```panic!()``` macro in rust aborts the program and can print an error message.

### Result

```Result``` is an enum that has two variants, ```Ok(T)``` and ```Err(E)```. Since resutl takes generic types, it can be used in many different situations. One example is

```
use std::fs::File;

fn main() {
    let greeting_file_result = File::open("hello.txt");

    let greeting_file = match greeting_file_result {
        Ok(file) => file,
        Err(error) => panic!("Problem opening the file: {:?}", error),
    };
}
```

where the error from the file read is printed in the panic. Since the error type from the filesystem can be matched as well, multiple error messages can be used in the code.

```
use std::fs::File;
use std::io::ErrorKind;

fn main() {
    let greeting_file_result = File::open("hello.txt");

    let greeting_file = match greeting_file_result {
        Ok(file) => file,
        Err(error) => match error.kind() {
            ErrorKind::NotFound => match File::create("hello.txt") {
                Ok(fc) => fc,
                Err(e) => panic!("Problem creating the file: {:?}", e),
            },
            other_error => {
                panic!("Problem opening the file: {:?}", other_error);
            }
        },
    };
}
```

We can use the ```unwrap()``` method to return the value in the Ok variant of the result, and panic if there is an error. The ```expect()``` method can be used to send a specific error message to send when panicing on an error.

*The ```?``` operator can be added to achieve error propagation in a consise way. If there is an error, the ```?``` will return the error from the function and not execute the rest of the function code.*

## Generic Types
