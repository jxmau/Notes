<h1> How to run test in Rust </h1>

<h2> In the same file </h2>

```rust

fn is_even(i : u32) -> bool {
    i % 2 == 0
}

#[cfg{test}]
mod test {

    // You can also repalce super by crate -> use crate::is_even;
    // You can also "invoke" all functions -> super::*;
    use super::is_even;

    #[test]
    fn lets_test_is_even() {
        // Two being an even number, it shall return true.
        assert_eq!(2, true) 
    }

}

```