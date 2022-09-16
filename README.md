# PI
rust 树莓派交叉编译

<br>
<br>

# cross compile 
https://chacin.dev/blog/cross-compiling-rust-for-the-raspberry-pi/  
https://medium.com/swlh/compiling-rust-for-raspberry-pi-arm-922b55dbb050  

```bash
cargo install --git https://github.com/cross-rs/cross
cross build --release --target arm-unknown-linux-gnueabihf
cross run --release --target arm-unknown-linux-gnueabihf
```

# 配置 Cross.toml
在项目根目录下  
```bash
touch Cross.toml
``` 
配置默认 target：  
> [build]  
> default-target = "arm-unknown-linux-gnueabihf"  

之后的  

```bash
cross build
``` 

等价于   
```bash
cross build --target arm-unknown-linux-gnueabihf
```  


