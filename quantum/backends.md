<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

# Thrush Programming Language

## Roadmap > Quantum Programming > Backends

This article briefly explains the availability of code generators and backends for generating quantum intermediary code.

------------------

### Q#

Q# is a programming language created by Microsoft to build software that supports quantum computing.

Many of the code backends they use to compile into an intermediary that supports execution on a real quantum computer are experimental. One of these is QIR, which comes from the QIR Alliance.

#### Q# Usage

For some reasons, we won't be using Q# for transpiling, instead using it as a bridge to quantum programming. In my opinion, it defeats the purpose of developing a language with LLVM, which is different from creating a fully transpiled language, like many others trying to "replace" C.

### QIR 

QIR is an intermediary language model that supports compiler development around LLVM, with support for a functional runtime with real-world executors available on quantum computers from IBM, Rigetti, and others.

Building quantum runtime support on top of LLVM IR is key, given its frequent use in code generators.

#### QIR Alliance

The [QIR Alliance](https://www.qir-alliance.org/) is a partnership of several major technology companies to advance the development of a cross-platform IR compiler with support for running on current or hypothetical quantum hardware.

For more information on QIR, see: `qir/README.md`

#### QIR Usage

The Thrush compiler will be fully compatible with QIR, as it is essentially LLVM IR, which can be issued using the same LLVM C API used to generate conventional code for conventional programming.

The only difference is that the FFI should be applied only to QIR runtime functions (QIS).