# linux memory management

## fundamental concepts

Every linux process has an address space that logically consists of 3 segments:

1. text segment

   * contains machine instructions
   * read only

2. data segment

   * initialized data
   * uninitialized data

3. stack segment
