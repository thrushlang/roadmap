<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

# Thrush Programming Language | Roadmap > Conventional Programming

This article will explain the biggest and most game-changing developments in mainstream programming that Thrush has to offer the world.

> [!WARNING]  
> These enormous development stages in the development of the language and compiler do not influence its early deployment to BETA.

## When will Thrush come out?

Thrush will be released when the compiler and language are deemed to have the minimum C capability to interoperate with core code. In addition, all the capabilities needed to interoperate with external code have been mapped, making Thrush an extensible and usable language with real code from other programming languages.

As of this writing, the compiler and language are not that far from this stage. Please be patient.

If you want to accelerate development, it is recommended to support the developer with technical or financial expertise.

In any case, Thrush is soon to be released.

------------------

### Cbindgen

A new feature in Thrush, this will allow the compiler to export C production code to native Thrush code, allowing for full C integration into Thrush.

For more information, see: `cbindgen/README.md`

### Compile Time Code Executation

A new feature of Thrush, which will allow code execution at compile time, enabling support for dynamic code execution. This bridges the current breachs in many programming languages ​​related to compile-time evaluation.

For more information, see: `compiletime/README.md`


------------------

## Highlight

### Cbindgen

This will allow Thrush to interoperate with production C code using just one import. This system preprocesses C type headers to integrate them into the Thrush compiler's front-end AST.

An example of its use can be seen as follows:

```rust
import "raylib.h";
```

### Compile Time Code Executation

It's an alternative compilation mode to Thrush's default AOT, without discontinuing its use. Compile-time execution can be performed in many programming languages. However, it is always limited to certain code scenarios. The code must always be static, not dynamic, so its capabilities are limited. This is the case in languages ​​like C++, Rust, and Zig.

Thrush will break these limits with a JIT implementation similar to dynamic languages ​​or those that use a JIT. This includes the ability to execute dynamic memory and external system operations.

An example of use is:

```rust
fn freee(any: ptr) void @public @extern("free");
fn malloc(size: u32) ptr @public @extern("malloc") @compiletime;

fn dynamic_code_allocation() ptr @compiletime {
    return malloc(sizeof(ptr));
}

fn main() u32 {

    local pointer: ptr = dynamic_code_allocation();

    free(pointer);

    return 0;

}
```

The JIT has the ability to replace all uses of the function with its value obtained in dynamic execution within the JIT, giving a constant value.