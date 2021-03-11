# Project Plan &ndash; Adding Sequences to P0 (Group 10)

> Authors: Afzal Chishti, Razi Syed, Sujan Kandeepan

## 0. Table of Contents

- [Project Plan &ndash; Adding Sequences to P0 (Group 10)](#project-plan--adding-sequences-to-p0-group-10)
  - [0. Table of Contents](#0-table-of-contents)
  - [1. Project Description](#1-project-description)
    - [1.1. General Project Overview](#11-general-project-overview)
    - [1.2. Proposed Language Features](#12-proposed-language-features)
    - [1.3. Memory Allocation Techniques](#13-memory-allocation-techniques)
    - [1.4. Implementation, Testing and Documentation](#14-implementation-testing-and-documentation)
  - [2. Resources](#2-resources)
    - [2.1. Memory Management Techniques](#21-memory-management-techniques)
    - [2.2. Python Lists and Memory](#22-python-lists-and-memory)
    - [2.3. WebAssembly References](#23-webassembly-references)
  - [3. Division of Work](#3-division-of-work)
    - [3.1. Afzal Chishti](#31-afzal-chishti)
    - [3.2. Razi Syed](#32-razi-syed)
    - [3.3. Sujan Kandeepan](#33-sujan-kandeepan)
  - [4. Weekly Schedule](#4-weekly-schedule)
    - [4.1. Week 1](#41-week-1)
    - [4.2. Week 2](#42-week-2)
    - [4.3. Week 3](#43-week-3)
    - [4.4. Week 4](#44-week-4)
    - [4.5. Week 5](#45-week-5)
    - [4.6. Week 6](#46-week-6)

## 1. Project Description

### 1.1. General Project Overview

The purpose of this project is to augment the P0 language to support sequences with a reasonable selection of sequence operations, as seen in other common programming languages, made available to the programmer.
Because sequences have unbounded size, they cannot be allocated on the stack and must instead be dynamically allocated in memory, which presents its own unique set of challenges.
Proposed additions to the P0 language, and approaches for handling memory allocation for this purpose, are explained below.

### 1.2. Proposed Language Features

Language features added to P0 will include but not be limited to the following:

- Sequence literals: `[]`, `[1, 2, 3]`
- Ranges as sequences: `[5 .. 10]`
- Sequence indexing: `x[3]`, `z[y + 2]`
- Selecting subsequences: `x[2:7]`, `y[3 : n + 1]`
- Sequence concatenation: `[1, 2] ++ [3, 4]`

More potential features, time permitting, may include the following:

- Prepend and append to sequences: `3 <| [4, 5, 6] |> 7`
- List (sequence) comprehension: `[x mod 3 for x in 1 .. 12]`
- Sequence iteration: `for i in [1 .. 10] do write(i)`

The above syntax takes inspiration from Python, Haskell and the notation used in CS/SE 2DM3 but remains flexible to changes during the process of development.

### 1.3. Memory Allocation Techniques

Two distinct approaches for handling memory allocation have been considered:

- Re-allocating contiguous memory buffers with new size calculated by a scale factor as the length of the sequence changes, similar to Java
  - Pros: constant-time array access, memory address arithmetic
  - Cons: costly re-allocation on resize, unused memory addresses
- Linked list internal representation with sparse memory allocation
  - Pros: constant-time resize operation, space-efficient
  - Cons: linear-time array access, no memory address arithmetic

The tentative decision is to use the first approach, considering that the cost of re-allocating memory is a fair trade-off to enable fast memory access for indexing.

### 1.4. Implementation, Testing and Documentation

Implementation and testing will be done using Jupyter notebooks by extending the current P0 syntax and compiler while writing tests in a similar manner to those seen in the course materials.
Documentation will be written using markdown format and published to the same repository as the source code.

## 2. Resources

### 2.1. Memory Management Techniques

...

### 2.2. Python Lists and Memory

4. Design and History FAQ. (n.d.). Retrieved March 10, 2021, from <https://docs.python.org/3/faq/design.html#how-are-lists-implemented-in-cpython>
5. Shaw, A. (2021, February 20). Your Guide to the CPython Source Code. Retrieved March 10, 2021, from <https://realpython.com/cpython-source-code-guide/#memory-management-in-cpython>

### 2.3. WebAssembly References

6. Rossberg, A. (n.d.). WebAssembly Specification. Retrieved March 10, 2021, from <https://webassembly.github.io/spec/core/>
7. WebAssembly. (n.d.). Retrieved March 10, 2021, from <https://developer.mozilla.org/en-US/docs/WebAssembly>

## 3. Division of Work

Based on the project description and researched materials given above, expected division of work per group member will be as outlined in the subsections below.

### 3.1. Afzal Chishti

...

### 3.2. Razi Syed

...

### 3.3. Sujan Kandeepan

- Augment P0 scanner, parser and evaluator to support sequences
- Design and implement compilation from P0 to WebAssembly
- Contribute toward documentation and presentation materials

## 4. Weekly Schedule

The tentative weekly schedule for this project is broken down in the following subsections and will remain flexible to changes over the remainder of the term.

### 4.1. Week 1

> Dates: Sunday, March 7 - Saturday, March 13

Priorities and action items:

- Complete project plan (this document) as outlined on Avenue
- Preliminary research into project topic, gathering resources
- Expand on general topic to develop complete problem statement
- Distribute work based on research findings and project requirements

Expected progress/completion:

- Project plan submitted for review/grading by Wednesday, March 10

### 4.2. Week 2

> Dates: Sunday, March 14 - Saturday, March 20

Priorities and action items:

- Set up codebase and organize into modular project structure
- Augment grammar and P0 scanner/parser to support new syntax
- Modify P0 evaluator to support new operations/expression types
- Research and implement memory allocation in WebAssembly

Expected progress/completion:

- High-level support for sequence language features added in P0
- Abstraction layer present for memory allocation in WebAssembly

### 4.3. Week 3

> Dates: Sunday, March 21 - Saturday, March 27

Priorities and action items:

- Develop high-level translation scheme from P0 to WebAssembly
- Implement sequences with supported operations in WebAssembly

Expected progress/completion:

- P0 syntax and WebAssembly implementation finished independently
- Compiler design for newly supported language features completed

### 4.4. Week 4

> Dates: Sunday, March 28 - Saturday, April 3

Priorities and action items:

- Implement compilation rules per translation scheme (integration)
- Create unit tests and integration tests using small P0 programs

Expected progress/completion:

- Mostly working compilation to accompany changes to P0 language
- Alpha stage in development pending extensive QA and optimizations

### 4.5. Week 5

> Dates: Sunday, April 4 - Saturday, April 10

Priorities and action items:

- Final testing and bug fixes with all functionality implemented
- Complete user instructions and documentation for all modules
- Work on presentation slides and poster to near completion

Expected progress/completion:

- Near-final version of project/presentation materials completed

### 4.6. Week 6

> Dates: Sunday, April 11 - Saturday, April 17

Priorities and action items:

- Finalize project submission, ensure project is accessible by TAs
- Prepare and rehearse presentation with required materials

Expected progress/completion:

- Complete project submitted and published by Monday, April 12
- Presentation delivered during tentative dates, materials submitted
