# C Programming Assignment 1

_data structures and pointers in the C language_

* * * 

## Goals

1. Learn to work with [Git](https://git-scm.com/) and [Github](https://github.com).
2. Practice development in the C programming language.
3. Practice explicit memory allocation and deallocation.
4. Practice working with _pointers_, raw references to memory locations, usually dynamically allocated.
5. Practice creating and manipulating data structures (arrays and `struct`s).
6. Practice writing algorithms for these data structures.
7. Prepare for [C2](https://github.com/ivogeorg/msl-clang-002).
8. Develop good coding style.

## Synopsis

This is a warmup assignment, meant to give you a problem which involves important features of the C language (pointers, dynamic memory allocation with `malloc` and deallocation with `free`, `struct` data structures), but is not in itself hard conceptually. You need to read in a file with English words and output a file where the words are counted and sorted. You are required to use _an unbalanced binary tree_ as the fundamental structure.

## Submission

You need to fork this repository and `git clone` it to your development environment. When you are done and your code works, `git commit` all your changes and `git push` to your forked (aka **remote**) repository. Work in the **master** branch. This assignment will not have a test suite like the following ones, so you don't have to install [cmocka](https://cmocka.org/). Your output will only be compared to the correct output.

### Github
Submissions are **one** per team. If you haven't done so, create a git account for your team. The name should look like **ucd-[course]-[team-color]-s18**. For example, **ucd-os-orange-s18** or **ucd-unix-black-s18**. (If you want, you can create an [organization](https://github.com/blog/674-introducing-organizations) but that might be overkill.) Make all team submissions from this account. 

### Canvas
Both team members have to make an assignment submission on [Canvas](https://canvas.instructure.com/courses/1270192) before the deadline. You only need to enter the _clone URL_ of your project repository (e.g. https://github.com/ivogeorg/msl-clang-001.git).

## Grading

### Points
50

### Details
This assignment has no test suite, so your grade is at the discretion of the instructor. Criteria:
1. Correctness
2. Performance
3. Style

## Due date

The assignment is due on **Sun, Jan 21, at 23:59 Mountain time**. The last commit to your repository before the deadline will be evaluated.

## Honor code

Free Github repositories are public so you can look at each other's code. Please, don't do that. You can discuss any programming topics and the assignments in general but sharing of solutions diminishes the individual learning experience of many people. Assignments might be randomly checked for plagiarism and a plagiarism claim may be raised against you. You definitely don't want that.

## Use of libraries

For this assignment, no external libraries should be used, except for the ANSI C Standard Library. The implementation of the data structures should be your own. We will use library implementations of data structures and programming primitives in the Pintos assignments.

## Coding style

Familiarize yourself with and start the following [coding style guide](http://courses.cms.caltech.edu/cs11/material/c/mike/misc/c_style_guide.html). While you are not expected to follow every point of it, you should try to follow it enought to get a feel for what is good style and bad style. C code can quickly become [unreadable](http://www.ioccc.org/) and difficult to maintain.

## References

The [C Reference](http://en.cppreference.com/w/c), which you should get confortable consulting.

The [ISO C Standards](http://www.iso-9899.info/wiki/The_Standard) defines the language. A freely available draft [C11 Standard](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf), if you want to dig deep.

This [C98 Library Reference](https://www-s.acm.illinois.edu/webmonkeys/book/c_guide/) seems to be the standard reference. You should not expect many changes, though it's always good to work off a latest copy of your library reference, which should be available through the vendor/implementor.

Two guides for implementation of `malloc()`: [here](http://danluu.com/malloc-tutorial/) and [here](http://www.inf.udec.cl/~leo/Malloc_tutorial.pdf).

## Detailed Instructions

### Input

The input will be a file containing a single line (i.e. no new lines) of all-lower-case English words. You need to read it in to sort them. The file will be in the same directory as your executable and will appear as the first argument when your program is run. To test input files are provided for you. A much larger file will be used in addition to test your program.

### Output

For each input file `input01.txt`, generate an output file in the same directory, called `myoutput01.txt`. Use the provided `output01.file` to compare against. The output should be an alphabetized list of unique words and their counts in the file, as follows:

```
one: 4
three: 5
years: 23
```

### Data structures

You should use a binary tree to keep the running count for words and keep them in alphabetical order. This means that if you have four words, say *one, two, three, go, one*, that come in this order, you will end up with a tree that looks like:

```
    one(2)
  /     \
 go(1)  two(1)
        /
     three(1)
```

Think what traversal you need to print the words in the tree in alphabetical order.

The tree has to be a *self-referential* C `struct`, containing a dynamically allocated `word`, its integer `count`, and pointers to the `left` and `right` subtrees. In other words, a tree is equivalent to a single node of the tree.

### Functionality

1. Read words from the file. Don't read in the whole file and then process it. Read it in chunks using a buffer.
2. Tree lookup for the next word in the input. 
3. If a word is in the tree, increment the count; if it isn't, dynamically allocate a new node; position and link it properly, and initialize the count to 1.
4. When you are done with the input, you should have a complete tree. Use it to print out the output file.
5. Destroy the tree, making sure you `free()` dynamic structures in the proper order.
6. Your tree functions should be *recursive*.

### README

Overwrite the **README.md** file and describe your project (approach, data structures, algorithms, etc.). Use this opportunity to get to know [*markdown*](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet). It's a useful skill.
