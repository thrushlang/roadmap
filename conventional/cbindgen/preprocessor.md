<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.6.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

# Thrush Programming Language 

## Roadmap > Conventional Programming > Cbindgen > Preprocessor

As an introduction to C-type header preprocessing, Thrush. You need to know a few details.

### Details / Issues

- Creating a .C header preprocessor tends to be very complex, not only due to the work of processing C syntax, but also the resolution of C macros and extensions that run at compile time.

- There are currently few usable production implementations in the parent language Rust.

- Macro preprocessing and compile-time expressions are very complex to do by default, which would lead the compiler to practically create another compiler within itself.

### Resolution

To have full support for preprocessing .h headers at compile time, you need to know that the easiest tool to integrate with the current LLVM backend is to use the Clang frontend for C.

The choice of clang to preprocess C header files is due to its robustness and ease of integration into the current Thrush compiler.

### Clang Library

There is a library around the Clang frontend, called `libclang` (for more information: https://clang.llvm.org/docs/LibClang.html), this can be used from Rust, from a present wrapper which is ``clang-sys`` crate (for more information: https://crates.io/crates/clang-sys).

This library exposes the entire current Clang frontend to the world, allowing you to manipulate and generate resolved ASTs from C-type headers.

### Resolution for C type headers

The solution is to fully integrate the Clang frontend into Thrush. This is entirely possible.

Once finished, the compiler will go through the following steps to process the AST of the C-type headers.

### Compilation Phases

------------

#### Type Preprocessing

C-type header resolution will be handled by the Clang frontend.

#### Compiler Organization

At this stage the Thrush compiler will sort and integrate the source C-type stack into the current compilation unit.

#### Code Generation

At this stage the Thrush compiler takes the organized AST in place and begins mapping it to Thrush intermediate types for the selected Thrush code generator.












 