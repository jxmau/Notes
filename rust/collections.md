# Vector


* Create a new vector 

```rust 

    // Create an empty vector for i32 type variables.
    // If the vector is not declared as mutacble,
    // you won't be able to push a var in the vec.
    let mut  vector : Vec<i32> = Vector::new();

    // Create a vector of i32 variables.
    // As the i32 is the default type for integer,
    // you don't need to specify like previously.
    let vector = vec![1, 2, 3, 4];


```

* Data manipulation

    - Add a var 

```rust 

    // mut is required to push variables in the vector.
    let mut vector : Vec<i32> = Vector::new();
    vector.push(1);
    vector.push(2);
    vector.push(3);
    // vector will be equal as [1, 2, 3]

```

    - Get a var

```rust

    let vector = vec![1, 2, 3]

    // Get a slice of a vector
    let mut var : &i32 = &vector[2];

```

# HashMap 

```rust

use std::collections::HashMap;

```
    * Create an HashMap

```rust 

    // Create an empty mutable HashMap
    let mut map = HashMap::new();

    // Create an immutable HashMap from two Vectors
    let last_name = vec![String::from("Bond"), String::from("Stark")];
    let first_name = vec![String::from("James"), String::from("Ned")];

    let names : HashMap<_, _> = last_name.inter_into().zip(first_name.into_inter()).collect();
    // Will get : {"Bond": "James", "Stark": "Ned"}

```

    * Data manipulation

        - Add

```rust 

    let mut map = HashMap::new();

    map.insert(String::from("Bond"), String::from("James"));
    map.insert(String::from("Stark"), String::from("Ned"));

```



