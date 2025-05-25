## FreeBSD kernel module in Rust

This repo is a fork of  https://github.com/nccgroup/freebsd-kernel-module-rust.
It will be used as an example for my GSoC project and possibly any future kernel level rust projects for FreeBSD. I am updating it when needed to ensure this works with current FreeBSD patches.

### Setup
* Install Rust via Rustup
* Be sure to have llvm15 installed, llvm17 or newer will not work (at least it didn't for me)
* Ensure to write `rustup component add rust-src` to your terminal
* Generate the kernel bindings:
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
