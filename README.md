# Rust Modbus
[![Build Status](https://travis-ci.org/hirschenberger/modbus-rs.svg)](https://travis-ci.org/hirschenberger/modbus-rs)
[![Clippy Linting Result](http://clippy.bashy.io/github/hirschenberger/modbus-rs/master/badge.png)](http://clippy.bashy.io/github/hirschenberger/modbus-rs/master/log)
[![Coverage Status](https://coveralls.io/repos/hirschenberger/modbus-rs/badge.svg?branch=master&service=github)](https://coveralls.io/github/hirschenberger/modbus-rs?branch=master)
[![](http://meritbadge.herokuapp.com/modbus)](https://crates.io/crates/modbus)
[![License](http://img.shields.io/:license-MIT-blue.svg)](http://doge.mit-license.org)


Modbus implementation in pure Rust.

## Usage
Add `modbus` to your `Cargo.toml` dependencies:

```toml
[dependencies]
modbus = "0.4"
```

Import the `modbus` crate and use it's functions:

```rust
use modbus::{Client, Coil};
use modbus::tcp;

let uid = 1; // Unit ID
let mut client = tcp::Transport::new("192.168.0.10", uid);

client.write_single_coil(1, Coil::On).unwrap();
client.write_single_coil(3, Coil::On).unwrap();

let res = client.read_coils(0, 5).unwrap();

// res ==  vec![Coil::Off, Coil::On, Coil::Off, Coil::On, Coil::Off];
```
See the [documentation](http://hirschenberger.github.io/modbus-rs/modbus/index.html) for usage examples and further reference and
the [examples](https://github.com/hirschenberger/modbus-rs/tree/master/examples) directory for a commandline client application.


## License
Copyright © 2015, 2016 Falco Hirschenberger

Distributed under the [MIT License](LICENSE).
