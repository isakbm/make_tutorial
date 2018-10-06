# Make Tutorial

This is essentially a copy of the 5th example from (colby)[http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/]

It is a very simple C project that contains the following files

hellomake.c
hellofunc.c
hellomake.h

Make is used to automate the compile and linking and makes it easy to organize the project
and its dependencies.

Lets have a look at the directory structure using tree, if you don't have tree

```terminal
sudo apt-get install tree 
```
Here's what it should look like

```terminal
$ tree make_tutorial
make_tutorial
├── include
│   └── hellomake.h
├── lib
└── src
    ├── hellofunc.c
    ├── hellomake.c
    ├── Makefile
    └── obj
```
Now let's run make from src and see what happens
```terminal
$ cd make_tutorial/src
$ make
gcc -c -o obj/hellomake.o hellomake.c -I../include
gcc -c -o obj/hellofunc.o hellofunc.c -I../include
gcc -o hellomake obj/hellomake.o obj/hellofunc.o -I../include -lm
$ ls
hellofunc.c  hellomake  hellomake.c  Makefile  obj
$ ./hellomake
Hello makefiles!
```
Now let's remove all the intermediate object files.
This is useful if you're done development and dont
want to waste space.
```terminal
$ ls obj
hellofunc.o  hellomake.o
$ make clean
rm -f obj/*.o *~ core /*~ 
$ ls obj
$
```
That's it, now adjust it to your own project and learn more about Make by reading the man pages.

