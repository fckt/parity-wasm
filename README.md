# parity-wasm

[![Build Status](https://travis-ci.org/NikVolf/parity-wasm.svg?branch=master)](https://travis-ci.org/NikVolf/parity-wasm)
[![crates.io link](https://img.shields.io/crates/v/parity-wasm.svg)](https://crates.io/crates/parity-wasm)

[Documentation](https://nikvolf.github.io/parity-wasm/parity_wasm/)

## Rust WebAssembly format serializing/deserializing

along with experimental interpreter

```rust

extern crate parity_wasm;

let module = parity_wasm::deserialize_file("./res/cases/v1/hello.wasm");
assert_eq!(module.code_section().is_some());

let code_section = module.code_section().unwrap(); // Part of the module with functions code

println!("Function count in wasm file: {}", code_section.bodies().len());
```

## Wabt Test suite

Interpreter and decoder supports full wabt testsuite (https://github.com/WebAssembly/testsuite), To run testsuite: 

- make sure you have all prerequisites to build `wabt` (since parity-wasm builds it internally using `cmake`, see https://github.com/WebAssembly/wabt)
- checkout with submodules (`git submodule update --init --recurive`)
- run `cargo test --release --manifest-path=spec/Cargo.toml`

# License

`parity-wasm` is primarily distributed under the terms of both the MIT
license and the Apache License (Version 2.0), at your choice.

See LICENSE-APACHE, and LICENSE-MIT for details.
