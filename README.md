#Clang and LLVM Tutorial
This archieve is mainly about some interesting examples of clang and llvm... Some of them  are the homework of my postgraduate course, some of them are others, most of them are `toy code` : )

## Contents
* AST Interpreter(#ast-interpreter)
* Function Pointer Pass(#function-pointer-pass)
* Value Range Analysis(#value-range-analysis)
* Data-Flow Analysis

### AST Interpreter
An interpreter of clang abstract syntax tree, toy code, now it only support integer type. It supports basic modules of programming language, e.g. ifstmt, whilestmt, function call, malloc and array... For more info, see [here...](https://github.com/lijiansong/clang-llvm-tutorial/tree/master/ast-interpreter)

### Function Pointer Pass
Implement of use-def chains based on the LLVM IR and bitcode, now it supports direct function calls and function pointer. For the case of function pointer, calculate the functions that may call, if it is determined, replace it with direct function call and write into the bitcode file. Also take the situation that the function pointers are stored in memory into consideration.

### Value Range Analysis
`Value range analysis` is a type of `data flow analysis` that tracks the range (interval) of values that a numeric variable can take on at each point of a program's execution. <br>
The resulting information can be used in optimizations such as `redundancy elimination, dead code elimination, instruction selection, etc`. But can also be used to improve the `safety of programs`, e.g. in the detection of buffer overruns. 
Techniques for value range analysis typically use `symbolic analysis` extensively. When it comes to the detailed implement, for each basic block, define the following data-flow equation：
```
in[B] = ∪out[A] | A∈ pred(B) && A！=S
out[B] = in[B]∪gen[B]
```

