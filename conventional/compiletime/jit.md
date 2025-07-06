<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

# Thrush Programming Language 

## Roadmap > Conventional Programming > Compile Time Code Execution > Just In Time Compiler

This article will briefly explain how the just-in-time compiler can be integrated into the current Thrush compiler, allowing Thrush to execute code at compile time.

### First things first.

It should be noted that we're talking about a JIT, not an implementation of some kind of interpreter with a virtual machine. Like many other programming languages, in this case, the JIT uses the current LLVM backend to compile code at compile time.

Exposed in Rust in the LLVM C API with the function:

```rust
pub unsafe extern "C" fn LLVMCreateJITCompilerForModule(
    OutJIT: *mut LLVMExecutionEngineRef,
    M: LLVMModuleRef,
    OptLevel: c_uint,
    OutError: *mut *mut c_char,
) -> LLVMBool
```

### JIT Compiler Design

First of all, the just-in-time compiler that will be integrated into the current Thrush compiler has high compile-time priority, which is executed before the final AOT execution by the same final compilation mode.

The C header type generator is processed before the compile-time execution of the JIT.

### JIT Compilation

JIT compilation will have an AOT phase that will begin compiling the entire representation marked with the `@compiletime` attribute into its intermediate representation. The frontend provides the entry point, where the scheduled base execution is marked. From this entry point, all future code that the JIT will process and execute will be executed.

### JIT Dynamic Symbol Table

One of Thrush's capabilities is dynamic code execution, which can generate system modifications, such as memory allocations and conventional processes in AOT mode. This puts it ahead of languages ​​like C++ and Rust, which have limited compile-time execution.

For this, a symbol table must be accessed dynamically that contains the **binary** and body of the functions needed to carry out a dynamic execution process in the JIT.

To achieve this, the compiler will link dynamic libraries at compile time, including the C runtime and the C standard library in its dynamic version (`.so` || `.dll`) for each operating system. At least in a standardized manner. Exotic targets will not include this support and will have to be resolved by the programmer using the command line.

### JIT Dynamic Types - Generation Type Symbol Resolution

For one of the most basic compile-time code execution functions, dynamic support requires the introduction of a compile-time FFI system.

This involves CBindgen external type generation and JIT's internal external type resolution.

This process may require assistance from the programmer, so the command line becomes essential.

For more information, see the article `typeres.md`.


