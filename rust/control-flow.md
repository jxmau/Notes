<h1> Rust's Control FLow </h1>

<h2> If </h2>


<h2> While </h2>

```rust
let number: u8 = 5;

while number != 0 {
    number -= 1;
}
```

<h2> For </h2>

Note : regarding range : 

```rust
for number in (1..5) {} // [1, 5[
for number in (1..=5) {} // [1, 5]
```

<h3> Reverse loop </h3>

```rust
let number: u8 = 5;

for number in (1..5).rev(){
    // (1..5) will describe an interval of [1, 5[
}


```