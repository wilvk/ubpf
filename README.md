# uBPF

Userspace eBPF VM

## About

This project aims to create an Apache-licensed library for executing eBPF programs. The primary implementation of eBPF lives in the Linux kernel, but due to its GPL license it can't be used in many projects.

[Linux documentation for the eBPF instruction set] (https://www.kernel.org/doc/Documentation/networking/filter.txt).

Currently this project includes an eBPF assembler, disassembler, partial
interpreter, and [instruction set reference](eBPF.md).

## Building

Run `make -c vm` to build the VM. This produces a static library `libubpf.a`
and a simple executable used by the testsuite.

## Compiling C to eBPF

You'll need Clang and LLVM 3.7.

    clang-3.7 -O2 -target bpf -c prog.c -o prog.o
    objcopy -I elf64-little -O binary prog.o prog.bin

You can then pass the contents of `prog.bin` to `ubpf_create`, or to the stdin of
the `vm/test` binary.

## Contributing

Please fork the project on GitHub and open a pull request. You can run all the
tests with `nosetests`.

## License

Copyright 2015, Big Switch Networks, Inc. Licensed under the Apache License, Version 2.0
<LICENSE-APACHE or http://www.apache.org/licenses/LICENSE-2.0>.
