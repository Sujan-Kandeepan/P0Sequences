# Documentation &ndash; Adding Sequences to P0 (Group 10)

> Authors: Afzal Chishti, Razi Syed, Sujan Kandeepan

## 0. Table of Contents
- [Documentation &ndash; Adding Sequences to P0 (Group 10)](#documentation--adding-sequences-to-p0-group-10)
  - [0. Table of Contents](#0-table-of-contents)
  - [1. Project Description](#1-project-description)
    - [1.1. General Project Overview](#11-general-project-overview)
    - [1.2. Language Features](#12-language-features)
    - [1.3. Grammar Changes](#13-grammar-changes)
    - [1.4 Implementation](#14-implementation)
  - [Testing](#testing)
    - [2.1 Passing testcases](#21-passing-testcases)
    - [2.2 Error checking testcases](#22-error-checking-testcases)
  - [3 Design Challenges](#3-design-challenges)
  - [4 References](#4-references)
## 1. Project Description

### 1.1. General Project Overview

The purpose of this project is to augment the P0 language to support sequences with a reasonable selection of sequence operations, as seen in other common programming languages, made available to the programmer.
Because sequences have unbounded size, they cannot be allocated on the stack and must instead be dynamically allocated in memory, which presents its own unique set of challenges.
Proposed additions to the P0 language, and approaches for handling memory allocation for this purpose, are explained below.

### 1.2. Language Features

Language features that were added to P0 are listed below:

- Sequence literals: `[]`, `[1, 2, 3]`
- Ranges as sequences: `[5 .. 10]`
- Sequence indexing: `x[3]`, `z[y + 2]`
- Selecting subsequences: `x[2:7]`, `y[3 : n + 1]`
- Sequence concatenation: `[1, 2] ++ [3, 4]`

The above syntax takes inspiration from Python, Haskell and the notation used in CS/SE 2DM3 but remains flexible to changes during the process of development.

### 1.3. Grammar Changes


### 1.4 Implementation

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


## 4 References
1. Rossberg, A. (n.d.). WebAssembly Specification. Retrieved March 10, 2021, from https://webassembly.github.io/spec/core/
2. WebAssembly. (n.d.). Retrieved March 10, 2021, from https://developer.mozilla.org/en-US/docs/WebAssembly
3. Design and History FAQ. (n.d.). Retrieved March 10, 2021, from https://docs.python.org/3/faq/design.html#how-are-lists-implemented-in-cpython
4. Ahn, H. (2021, March 31). WebAssembly/bulk-memory-operations. Retrieved April 14, 2021, from https://github.com/WebAssembly/bulk-memory-operations/blob/master/proposals/bulk-memory-operations/Overview.md
5. Conrad Watt, Andreas Rossberg, and Jean Pichon-Pharabod. 2019. Weakening WebAssembly. Proc. ACM Program. Lang. 3, OOPSLA, Article 133 (October 2019), 28 pages. https://doi.org/10.1145/3360559