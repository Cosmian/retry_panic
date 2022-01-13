retry_panic
===========

This macro allows a function to be restarted once if it panics.

For example, it can be useful when running tests that may fail where it is *accepted*.

Warning: remember that a panicking function is a problem that should be addressed.

```rust
use rand::prelude::*;

#[retry_panic]
#[test]
fn test_get_odd_number() {
    let mut rng = rand::thread_rng();
    let y: u32 = rng.gen();
    if y % 2 == 0 {
        panic!("even number !");
    }
}
```