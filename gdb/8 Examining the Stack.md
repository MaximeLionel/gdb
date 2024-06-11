* Stack Frame - Each time your program performs a function call, information about the call is generated. That information includes the location of the call in your program, the arguments of the call, and the local variables of the function being called. The information is saved in a block of data called a stack frame.

# 8.1 Stack Frames
* The **call stack** is divided up into contiguous pieces called **stack frames**, or frames for short; each frame is the data associated with one call to one function.
	* When your program is started, the stack has only one frame, that of the function main. This is called the **initial frame** or the **outermost frame**.
	* Each time a function is called, a new frame is made. Each time a function returns, the frame for that function invocation is eliminated.
	* If a function is recursive, there can be many frames for the same function.
	* The frame for the function in which execution is actually occurring is called the **innermost frame**.
* Frame pointer register - A stack frame consists of many bytes, each of which has its own address; each kind of computer has a convention for choosing one byte whose address serves as the address of the frame. Usually this address is kept in a register called the **frame pointer register**, while execution is going on in that frame.
* gdb labels each existing stack frame with a level, a number that is zero for the innermost frame, one for the frame that called it, and so on upward.
* Some compilers provide a way to compile functions so that they operate without stack frames: gcc - `-fomit-frame-pointer`.

# 8.2 Backtraces
## Syntax
```shell
backtrace [option]... [qualifier]... [count]
bt [option]... [qualifier]... [count]
```
* A backtrace is a summary of how your program got where it is. 
	* It shows one line per frame, for many frames, starting with the currently executing frame (frame zero), followed by its caller (frame one), and on up the stack.

## Optional \[count\]
* n:  Print only the innermost n frames, where n is a positive number.
* -n: Print only the outermost n frames, where n is a positive number.

## Optional \[option\]
* -full: Print the values of the local variables also. This can be combined with the optional count to limit the number of frames shown.

* -no-filters: This is only relevant when gdb has been configured with Python support.

* -hide: A Python frame filter might decide to “elide” some frames. Normally such elided frames are still printed, but they are indented relative to the filtered frames that cause them to be elided. The `-hide` option causes elided frames to not be printed at all.


