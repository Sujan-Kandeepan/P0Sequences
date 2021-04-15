# Adding Sequences to P0 (Group 10)

> Authors: Afzal Chishti, Razi Syed, Sujan Kandeepan

## Overview

This project builds on the existing P0 language and compiler to support sequences by building on the existing array type which now supports the following language features:

- Array literals: `[]`, `[1, 2, 3]`
- Ranges as arrays: `[5..10]`
- Array indexing: `x[3]`, `z[y + 2]`
- Selecting subarrays: `x[2:7]`, `y[3 : n + 1]`
- Array concatenation: `[1, 2] + [3, 4]`

See [documentation.md](documentation.md) to learn more about this project and the work involved.

## Source code

This project implementation builds on the P0 language and compiler provided in Lab 10 without any new files needing to be added to the source code.

Changes were made to the following files in the implementation of this project: [CGast.ipynb](CGast.ipynb), [CGwat.ipynb](CGwat.ipynb), [P0.ipynb](P0.ipynb), and [ST.ipynb](ST.ipynb).

[SC.ipynb](SC.ipynb) required no modifications as the updated grammar to support sequences did not include any new symbols.

Full documentation of these changes can be found in [documentation.md](documentation.md).

## Testing

A testing playground for experimenting, debugging, and running automated tests is made available in the following files: [TestConcat.ipynb](TestConcat.ipynb), [TestIndexing.ipynb](TestIndexing.ipynb), and [TestLiterals.ipynb](TestLiterals.ipynb).

Further information on these testing modules is given in [documentation.md](documentation.md).
