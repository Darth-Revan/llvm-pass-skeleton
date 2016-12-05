# llvm-pass-skeleton
A generic skeleton for building your own optimization passes for the awesome LLVM Project

## Introduction

This simple skeleton can be used to write your own optimizer passes for the LLVM without building the LLVM itself. You only need to place the skeleton somewhere on your hard drive, write your Pass and build it with CMake and your favorite C++ compiler.

## Prerequisites

In order to use this skeleton, you have to install the LLVM and its development headers on your system. I strongly recommend to do this with your package manager if you're on Linux.

Additionally you need an up-to-date version of CMake and a C\+\+11-compliant compiler (the LLVM makes heavy use of the nice features of C\+\+11). I personally like to use Clang, but GCC or the Microsoft Visual C\+\+ Compiler should work perfectly well.

## Usage

Simply clone the repo to a location of your choice and change to that directory:

```
git clone https://github.com/Darth-Revan/llvm-pass-skeleton.git
cd llvm-pass-skeleton
```

The structure of the directory is the following:

```
llvm-pass-skeleton/
+-- build
+-- CMakeLists.txt
+-- LICENSE
+-- MyPass
│   +-- CMakeLists.txt
│   \-- MyPass.cpp
\-- README.md
```

You may change the folder *MyPass* to whatever you like, but remember to change the last line in *llvm-pass-skeleton/CMakeLists.txt* accordingly. The same applies to *llvm-pass-skeleton/MyPass/MyPass.cpp* and *llvm-pass-skeleton/MyPass/CMakeLists.txt* respectively.

Your C\+\+ code goes into *MyPass.cpp*. You may also add some additional header and source code files in the same directory.

If you're ready to compile your pass, change to the *build* directory and execute *cmake*. On my system (Ubuntu 16.04 LTS) I have to specify the LLVM_DIR manually (which is the directory, where the file *LLVMConfig.cmake* is located):

```
cmake -DLLVM_DIR=/usr/lib/llvm-3.9/lib/cmake/llvm ..
```

*CMake* then generates the Build-files according to your system (on Linux these will be good old Unix Makefiles). Then build the pass with

```
make
```

and your newly created pass is ready to use as a shared library in *build/MyPass*.

## Further Reading

For some good guidance on how to write a pass and how to use LLVM's awesome programming interface please consult the official documentation and especially the nice article [Writing an LLVM Pass](http://llvm.org/docs/WritingAnLLVMPass.html).

## License

This small skeleton is provided under the terms of the MIT License. To make things short: Do what you like to do with it.
