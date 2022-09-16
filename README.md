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


# binary size 问题

[Why are Rust executables so huge?](https://stackoverflow.com/questions/29008127/why-are-rust-executables-so-huge)  
[Size of the executable binary file of an application](https://users.rust-lang.org/t/size-of-the-executable-binary-file-of-an-application/62160/16)  

rust 编译出来的二进制文件 size 很大，即便是 release 版的 hello world 也有 3M 以上！！  

开优化：  
> [profile.release]  
> opt-level = 'z'     # Optimize for size.  
> lto = true          # Enable Link Time Optimization  
> codegen-units = 1   # Reduce number of codegen units to increase optimizations.  
> panic = 'abort'     # Abort on panic  
> strip = true        # Strip symbols from binary*  

优化后，从 8M 降到了 240K， 跟 gcc 编出来的 8K 还是差很远呢！！   


