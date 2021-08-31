<h1> Rust's Input - Output Library </h1>

<h2> How to read a line </h2>

```rust
use std::io::{self, Read};

fn main() {
     
    let mut input = String::new(); 
    match io::stdin().read_line(&mut input){
        Ok(n) => {
            println!("{} bytes read", n);
            println!("{}", input);
        }
        Err(error) => println!("error : {}", error),
    }

}
```