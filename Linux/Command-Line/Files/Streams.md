---
title: File Streams
parent: Files
grand_parent: Command Line Operations
---

# Standard file streams

When commands are executed, by default there are three standard file streams (or descriptors) always open for use: standard input (standard in or `stdin`), standard output (standard out or `stdout`) and standard error (or `stderr`).

> `stdin` is normally the keyboard, `stdout` the terminal and `stderr` to a log file

In Linux, all open files are represented internally by what are called file descriptors. Simply put, these are represented by numbers starting at zero. `stdin` is file descriptor `0`, `stdout` is file descriptor `1`, and `stderr` is file descriptor `2`.

## IO Redirection

These streams can be redirected to:
- Read input from a file instead of the keyboard
- Output to a file instead of the screen
- Redirect the error messages

To redirect the input

```bash
command < input_file
```

For the output (and the standard error), `>` can be used, in combination with the file descriptor:
```bash
command > output_file # Redirects stdout
command 1> output_file #Same but with file descriptor
command 2> log_file # Redirects stderr
command > all_output_file 2>&1 #Both stdout and stderr to the same file
command >& all_output_file #Same as above, only in BASH
```
