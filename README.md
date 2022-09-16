
## cross compile 
https://chacin.dev/blog/cross-compiling-rust-for-the-raspberry-pi/
https://medium.com/swlh/compiling-rust-for-raspberry-pi-arm-922b55dbb050

```bash
cargo install --git https://github.com/cross-rs/cross
cross build --release --target arm-unknown-linux-gnueabihf
cross run --release --target arm-unknown-linux-gnueabihf
```

