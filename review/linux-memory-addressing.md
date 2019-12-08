# linux memory management

## process memory regions

Every linux process has an address space that logically consists of 3 segments:

1. text segment

contains machine instructions and read only

2. data segment

contains all the program's variables, strings, arrays, and other data.

   * initialized data: static variables, global variables.
   * uninitialized data(BSS): uninitialized global variables. It is set to point to the static zero page, a write-protected page full of zeros, when the process is loaded.

executable file = short header + text segment + initailized data

3. stack segment

contains all the environment(shell) variables and local variables. It starts at or near the top of the virtual address space and grows down towrad 0.

[mm_struct](https://elixir.bootlin.com/linux/v5.4/source/include/linux/mm_types.h#L370), a memory descriptor includes some fields identifying the role of som memory regions.

## implementation of memory management in Linux

## references

1. Modern Operating Systems (Forth Edition) 10.4
