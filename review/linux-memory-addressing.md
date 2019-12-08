# linux memory management

## fundamental concepts

Every linux process has an address space that logically consists of 3 segments:

1. text segment

contains machine instructions and read only

2. data segment

contains all the program's variables, strings, arrays, and other data.

   * initialized data
   * uninitialized data(BSS). It is set to point to the static zero page, a write-protected page full of zeros, when the process is loaded.

executable file = short header + text segment + initailized data

3. stack segment

contains all the environment(shell) variables and starts at or near the top of the virtual address space and grows down towrad 0.

## implementation of memory management in Linux

## references

1. Modern Operating Systems (Forth Edition) 10.4
