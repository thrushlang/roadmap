<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

# Thrush Programming Language

## Roadmap > Quantum Programming > Backends > QIR

This short article specifies the useful functions and tools that QIR has for use with the Thrush compiler.

------------------

### QAT

The QIR Adapter Tool is a compiler and toolkit for manipulating, maintaining, and optimizing QIRs. This tool allows us to explicitly manipulate IR and optimize it with passes. It is equivalent to the ``opt`` project in LLVM.

For more information, see: https://github.com/qir-alliance/qat

#### QAT Usage

We can use the QIR Adapter Tool in the Thrush compiler for a dedicated optimization phase that allows us to optimize the IR for a specific purpose.

#### QAT Installation

One way we can do this is for the Thrush compiler to include a certain version of the compiler compressed in .xz or .zip format in its binary. The first build Thrush makes will be used to install the tool on the current system, if there is a quantum target.

### QIR Runner

QIR Runner is a tool developed by the QIR Alliance to run QIR conventionally on conventional machines. It emulates QIR's operation on a real quantum computer, using a backend, runtime, and virtual machine already integrated into the tool.

For more information, see: https://github.com/qir-alliance/qir-runner

#### QIR Usage

The tool is primarily written in Rust, the parent language of the Thrush compiler, so its integration will be simple.

To accomplish this, you can include the QIR Runner. When you specify the command line to emit the QIR and emulate it, ``-emulate``, this will trigger the QIR as soon as the compiler emits the QIR, whether optimized or not by QAT.

#### QIR Installation

QIR Runner may already be part of the Thrush compiler. Otherwise, it will be compressed, embedded in the Thrush compiler executable, and the first build on the system will install QIR Runner in an external path.
