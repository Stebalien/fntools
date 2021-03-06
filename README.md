Tool
=====

A grab-bag of useful functions for functional programming.

* Docs: https://docs.rs/tool/
* Build Status: [![Build Status](https://travis-ci.org/Stebalien/tool-rs.svg?branch=master)](https://travis-ci.org/Stebalien/tool-rs)
* Crate: [tool](https://crates.io/crates/tool)

## Example

### Non-empty strings

```rust
extern crate tool;
use tool::prelude::*;
fn main() {
    let strings: Vec<_> = vec!["my string", "", "asdf", ""]
        .into_iter()
        .filter(non_empty)
        .collect();
    assert_eq!(strings, vec!["my string", "asdf"]);
}
```

### First item in an iterator of tuples.

```rust
extern crate tool;
use tool::prelude::*;
fn main() {
    let strings: Vec<_> = vec![("first", 1), ("second", 2), ("third", 3), ("fourth", 4)]
        .into_iter()
        .map(first)
        .collect();

    assert_eq!(strings, vec!["first", "second", "third", "fourth"]);
}
```

## Compile-Time Flags (cargo features)

* `use_std` (default: enabled) - Disable this if you're project doesn't depend on libstd.
