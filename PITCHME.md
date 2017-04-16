---
## Programming Paradigms

#### Matthew Morris
#### April 20, 2017
---
### Paradigms

* Structured
  * Imperative
    * Procedural
    * Object-oriented
  * Declarative
    * Functional
    * Logic
---
### Machine Code

```
10111010 01100110 00000000 00000011 00000000 00000000 10111001 01100110
00000000 00100100 00000000 00000000 10111011 01100110 00000000 00000001
00000000 00000000 10111000 01100110 00000000 00000100 00000000 00000000
10000000 11001101 10111000 01100110 00000000 00000001 00000000 00000000
10000000 11001101 00000000 00000000 00110100 00110010 00000000 00001010
```
---
### Machine Code - Hexadecimal

```
10111010 01100110 00000000 00000011 00000000 00000000 10111001 01100110
00000000 00100100 00000000 00000000 10111011 01100110 00000000 00000001
00000000 00000000 10111000 01100110 00000000 00000100 00000000 00000000
10000000 11001101 10111000 01100110 00000000 00000001 00000000 00000000
10000000 11001101 00000000 00000000 00110100 00110010 00000000 00001010
```

```
0000000 ba66 0003 0000 b966 0024 0000 bb66 0001
0000020 0000 b866 0004 0000 80cd b866 0001 0000
0000040 80cd 0000 3432 000a
0000047
```
---
### Assembly Language

``` x86asm
section .data
    msg db '24', 10     ; the string '24', followed by a newline (10) character
    len equ $ - msg     ; the length of msg

section .text
    global _start

_start:
    ; Print message 
    mov edx, len                ; message length
    mov ecx, msg                ; message to write 
    mov ebx, 1          ; file descriptor (stdout)
    mov eax, 4          ; system call number (sys_write)
    int 80h             ; kernel interrupt

    ; Exit
    mov eax, 1          ; system call number (sys_exit)
    int 80h             ; kernel interrupt
```
---
### Unstructured Programming

Tiny BASIC:

``` basic
10 LET N=1 
20 PRINT N
30 LET N=N+1
40 IF N<25 GOTO 20
50 END
```

Assembly Language, Fortran, BASIC, ...

Most of these languages can be written in a structured style these days.
---
### Questions?
