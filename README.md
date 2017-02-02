## Operating Systems Concepts: Programming Assignment C1

_data structures and pointers in the C language_

* * * 

### Goals

1. Practice development in the C programming language.
2. Practice explicit memory allocation and deallocation.
3. Practice creating and manipulate data structures (arrays and `struct`s).
4. Practice working with pointers.
4. Practice writing algorithms for these data structures.
5. Prepare for [C2](https://github.com/ivogeorg/msl-clang-002).
6. Develop good coding style.

### Synopsis

This is a warmup assignment, meant to give you a problem which involves major features of the C language but is not hard in itself. You need to read in a file with English words and output a file where the words are counted and sorted. You need to use a binary tree as the fundamental structure.

### Submission

You need to fork this repository and `git clone` it to your development machines. When you are done and your code works, `git commit` all your changes and `git push` to your forked (aka **remote** repository. Work in the **master** branch. This assignment will not have a test suite like the following ones, so you don't have to install [cmocka](https://cmocka.org/). Your output will only be compared to the correct output.

Submissions are **one** per team. If you haven't done so, create a git account for your team. The name should look like **msl-os-[color]-[school]-[term]**. For example, **msl-os-orange-msud-s17** or **msl-os-black-ucd**. (If you want, you can create an [organization](https://github.com/blog/674-introducing-organizations) but that might be overkill.) Make all team submissions from this account. 

### Grading

This assignment is pass/fail and carries no score. Note that good coding style will be important for further assignments so use this opportunity to develop it.

### Due date

The assignment is due on **Mon, Feb 6, at 23:59 Mountain time**. The last commit to your repository before the deadline will be graded.

### Honor code

Free Github repositories are public so you can look at each other's code. Please, don't do that. You can discuss any programming topics and the assignments in general but sharing of solutions diminishes the individual learning experience of many people. Assignments might be randomly checked for plagiarism and a plagiarism claim may be raised against you.

Note that PA1 one is an _individual_ assignment, not a _team_ assignment like the upcoming Pintos assignments.

### Use of libraries

For this assignment, no external libraries should be used, except for the ANSI C Standard Library. The implementation of the data structures should be your own. We will use library implementations of data structures and programming primitives in the Pintos assignments.

### Coding style

Familiarize yourself with and start the following [coding style guide](http://courses.cms.caltech.edu/cs11/material/c/mike/misc/c_style_guide.html). While you are not expected to follow every point of it, you should try to follow it enought to get a feel for what is good style and bad style. C code can quickly become [unreadable](http://www.ioccc.org/) and difficult to maintain.

### References

A minimal [C Reference](https://cs50.harvard.edu/resources/cppreference.com/), which should be sufficient for your needs.

The [C98 Library Reference](https://www-s.acm.illinois.edu/webmonkeys/book/c_guide/) is more complete.

The [C11 Standard](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf) is just provided for completeness, and you shouldn't need to read it, except peruse it out of curiosity.

Two guides for implementation of `malloc()`: [here](http://danluu.com/malloc-tutorial/) and [here](http://www.inf.udec.cl/~leo/Malloc_tutorial.pdf).

### Detailed Instructions

#### Input

The input will be a file containing a single line (i.e. no new lines) of all-lower-case English words. You need to read it in to sort them. The file will be in the same directory as your executable and will appear as the first argument when your program is run. To test input files are provided for you. A much larger file will be used in addition to test your program.

#### Output

For each input file `input01.txt`, generate an output file in the same directory, called `myoutput01.txt`. Use the provided `output01.file` to compare against. The output should be an alphabetized list of unique words and their counts in the file, as follows:

```
one: 4
three: 5
years: 23
```

#### Data structures

You should use a binary tree to keep the running count for words and keep them in alphabetical order. This means that if you have four words, say *one, two, three, go, one*, that come in this order, you will end up with a tree that looks like:

    one(2)
  /     \
 go(1)  two(1)
        /
     three(1)
   
Think what traversal you need to print the words in the tree in alphabetical order.

The tree has to be a *self-referential* C `struct`, containing a dynamically allocated `word`, its integer `count`, and pointers to the `left` and `right` subtrees. In other words, a tree is equivalent to a single node of the tree.

#### Functionality

