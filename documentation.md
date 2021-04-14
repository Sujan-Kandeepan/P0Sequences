# Documentation &ndash; Adding Sequences to P0 (Group 10)

> Authors: Afzal Chishti, Razi Syed, Sujan Kandeepan

## 0. Table of Contents
- [Documentation &ndash; Adding Sequences to P0 (Group 10)](#documentation--adding-sequences-to-p0-group-10)
  - [0. Table of Contents](#0-table-of-contents)
  - [1. Project Description](#1-project-description)
    - [1.1. General Project Overview](#11-general-project-overview)
    - [1.2. Language Features](#12-language-features)
    - [1.3. Grammar Changes](#13-grammar-changes)
        - [P0:](#p0)
        - [ST](#st)
    - [1.4 Implementation](#14-implementation)
  - [Testing](#testing)
    - [2.1 Passing testcases](#21-passing-testcases)
    - [2.2 Error checking testcases](#22-error-checking-testcases)
  - [3 Design Challenges](#3-design-challenges)
  - [4 Conclusion](#4-conclusion)
  - [5 References](#5-references)
## 1. Project Description

### 1.1. General Project Overview

The purpose of this project is to augment the P0 language to support sequences which are a data type with dynamic size with a reasonable selection of sequence operations, as seen in other common programming languages, made available to the programmer.As sequences have unbounded size, they cannot be allocated on the stack and must instead be dynamically allocated in memory, which presents its own unique set of challenges. Our additions to the P0 language and approach for handling memory allocation for this purpose, are explained below.

### 1.2. Language Features

Language features that were added to P0 are listed below:

- Array literals: `[]`, `[1, 2, 3]`
- Ranges as arrays: `[5 .. 10]`
- Array indexing: `x[3]`, `z[y + 2]`
- Selecting subarrays: `x[2:7]`, `y[3 : n + 1]`
- Array concatenation: `[1, 2] ++ [3, 4]`

The above syntax takes inspiration from Python, Haskell and the notation used in CS/SE 2DM3 but remains flexible to changes during the process of development.

### 1.3. Grammar Changes

##### P0:
So, the procedure *selection()* is added to so that it can support subarrays by having the `[: expression]` added in the grammar rule below. 

```
selector ::= { [ expression [: expression] ] | . ident }
```

The restrictions with using subarrays is stated below
- Indexes must be integers
- Start and end index must be in bound
- Start index must be lower than end index

In addition, the procedure *factor()* has `"[" [expression ({"," expression} | ".." expression)] "]" [selector]` added to it.  The `[expression ({"," expression})]` is to represent the adding of passing literal arrays such as `a = [1, 3, 7]`. The major restriction for creating an arrayliteral using this method is that all the elements must be of the same type. 

The `[expression (".." expression)]` is to add the functionality of passing a range such as `a = [1 .. 5]`. The restrictions here is the fact that the range must contain integer values and the value prior to `..` must be lower than or equal to the value after the `..`. 

##### ST
Two new types of symbol table entries were created which are **ArrayLiteral** and **SubArray**.
The ArrayLiteral is the class for when creating a new literal whether by passing every value (eg. `a = [2,6,-5]`) or by using ranges (eg. `a = [5 .. 8]`) to pass the values. 

Subarrays are for the purpose like the name suggests for when a user attempts to get a portion of an existing array. 

Both of the above types augment the array type and are references to the array type.
### 1.4 Implementation
We decided to augment existing array type instead of defining new sequence type. To do so, there was extension to the language syntax to support new language features. The parser was modified to accept new syntax and update grammar and alongside it a comprehensive error handling was also introduced for handling the new syntax rules. Array literals and subarrays were new types that referenced to original array. In addition to persevere memory and have good performance, duplicating array contents into new memory locations was avoided. The new types/constructors resulted in better code readability. To provide operations such as concatenation and sub array, the existing operators were overloaded.
Eg. ‘:=’ for populating entire arrays, ‘+’ for concatenation



The memory allocation aspect which is paramount especially for the concatenation aspect is done by the *genCopyArray* in `CGwats.ipynb` and is shown below.

```

```

For the sake of comparison, a new procedure called `genStandAloneOp()` was created and is shown below.

```
def genStandaloneOp(op):
    asm.append('i32.and' if op == AND else \
            'i32.or' if op == OR else '?')
    x = Var(Bool); x.lev = Stack
    return x
```
As a result of the above, to keep the remaining code consistent an optional *load* parameter was added to the *genUnaryOp*, *genBinaryOp* and *genRelation* and set to true to indicate that for all those instances to ensure code still runs as it did before.


## Testing
The testing of new functionality is shown in the **TestConcat.ipynb**, , and

### 2.1 Passing testcases
It is important to have testcases that are used to validate the above features and examples that we showed in section 1.2. There are numerous tests in each of the test files which are used for validating the features. 

In **TestConcat.ipynb**, there are __ testcases that are for meant to pass and check valid syntax.


In ****, there are __ testcases that are for meant to pass and check valid syntax.

In ****, there are __ testcases that are for meant to pass and check valid syntax.

### 2.2 Error checking testcases
In addition to having checked that the features have been added properly,it is important to see in what scenario the new grammar rules fail and also what error message is returned so that a user can easily discern what the issue is. 

In **TestConcat.ipynb**, there are __ testcases that are for meant to fail and result in an error message.

In ****, there are __ testcases that are for meant to fail and result in an error message.

In ****, there are __ testcases that are for meant to fail and result in an error message.

## 3 Design Challenges
1) Deciding how we would implement sequences in terms of whether to create a new data type or just add to the array data type
**End result:** After seeing in lab 11, that arrays already provided much of the groundwork necessary in terms of the fact that the value at an index can be updated one at a time. We decided that we could re-use arrays in many scenarios as we do in the `SubArray` in the **ST.ipynb** class as shown below.  

```
class SubArray:
    def __init__(self, array, lower, upper):
        self.array, self.lower, self.upper = array, lower, upper
    def __str__(self):
        return 'Array(array = ' + str(self.array) + ', lower = ' + \
               str(self.lower) + ', upper = ' + str(self.upper) + ')'
```



2) How to allocate memory when doing concatenation of array or subarrays
**End result:** After much delibaration and research in terms of how to allocate memory in a manner in such a way that memory leak could be reduced to a minimum in which we discussed ideas of declaring size of new array prior to concatenation. In addition, as part of this we discussed how allocating memory to an array out of bounds would work. After discussion with TA it was clarified that the memory leak would not be in the scope of this project and would be handled by a garbage collector. 

1) 

## 4 Conclusion

## 5 References
1. Rossberg, A. (n.d.). WebAssembly Specification. Retrieved March 10, 2021, from https://webassembly.github.io/spec/core/
2. WebAssembly. (n.d.). Retrieved March 10, 2021, from https://developer.mozilla.org/en-US/docs/WebAssembly
3. Design and History FAQ. (n.d.). Retrieved March 10, 2021, from https://docs.python.org/3/faq/design.html#how-are-lists-implemented-in-cpython
4. Ahn, H. (2021, March 31). WebAssembly/bulk-memory-operations. Retrieved April 14, 2021, from https://github.com/WebAssembly/bulk-memory-operations/blob/master/proposals/bulk-memory-operations/Overview.md
5. Conrad Watt, Andreas Rossberg, and Jean Pichon-Pharabod. 2019. Weakening WebAssembly. Proc. ACM Program. Lang. 3, OOPSLA, Article 133 (October 2019), 28 pages. https://doi.org/10.1145/3360559