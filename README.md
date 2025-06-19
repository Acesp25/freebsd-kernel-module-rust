## FreeBSD kernel module in Rust

This repo is a fork of  https://github.com/nccgroup/freebsd-kernel-module-rust.
It will be used as an example for my GSoC project and possibly any future kernel level rust projects for FreeBSD. I am updating it when needed to ensure this works with current FreeBSD patches.

This has been tested with 1.90.0-nightly (667787527 2025-07-02)

### Setup
* Install Rust via Rustup
* Install llvm19
* Do `rustup component add rust-src`
* Generate the kernel bindings by doing:
```bash
cargo build -p kernel-sys --target x86_64-unknown-freebsd
```

### Run

```bash
./build.sh
sudo make load
echo "hi rust" > /dev/rustmodule
cat /dev/rustmodule
sudo make unload
```

### Licence
This source code is provided under the terms of the [BSD 2-Clause licence](LICENSE.txt)
and is based on [public-domain work](https://github.com/johalun/echo) by Johannes Lundberg.
