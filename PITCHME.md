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
    mov edx, len        ; message length
    mov ecx, msg        ; message to write 
    mov ebx, 1          ; file descriptor (stdout)
    mov eax, 4          ; system call number (sys_write)
    int 80h             ; kernel interrupt

    ; Exit
    mov eax, 1          ; system call number (sys_exit)
    int 80h             ; kernel interrupt
```
---
### Development of High-level Languages

- 1948 **Plankalkül** (high-level, concept only)
- 1949 **EDSAC assembler** (one-to-one opcode mnemonics)
- 1949 **Short Code** (high-level mathematical expressions)
- 1952 **Autocode** (compiled; abstracted groups of opcodes for e.g. printing)
- 1957 **Fortran** (optimizing compiler; IF, DO, GO TO) 
---
### Development of High-level Languages (cont.)

- 1958 **Fortran II** (subroutines and functions)
- 1958 **ALGOL 58** (compound statements, FOR loops, assignment ≠ equality)
- 1958 **Lisp** (homoiconic, macros, recursion, anonymous functions, conditionals) 
- 1959 **COBOL** (natural language programming, records/structs)
- 1960 **ALGOL 60** (code blocks, nested functions, lexical scoping, IF-THEN-ELSE)
---
### Unstructured Programming

Tiny BASIC:

```
10 LET N=1 
20 PRINT N
30 LET N=N+1
40 IF N<25 GOTO 20
50 END
```
---
### Unstructured Programming Languages

Assembly Language, Fortran, COBOL, BASIC, ...

Most of these languages can be written in a structured style these days.
---
### Structured Programming

- **1960** ALGOL 60 (subroutines, blocks, FOR, WHILE, IF-THEN-ELSE)
- **1966** structured program theorem, Böhm and Jacopini 
- **1968** "A Case against the GO TO Statement", Dijkstra 
- **1969** *Notes on Structured Programming*, Dijkstra 

Basic control structures: sequence, selection, iteration
---
### Procedural Programming
---?image=assets/634px-Mai_Chau_-_Hausbau.jpg
---
### Examples

C:
``` c
#include "stdio.h"

int main(void) {
    int n;

    for (n = 1; n <= 24; n++) {
        printf("%d\n", n);
    }
    return 0;
}
```

Python:
``` python
for n in range(1,25):
    print(n)
```
---
### Procedural Programming Languages

ALGOL, C, Pascal, Ada, ... 

Some object-oriented languages can be written in a procedural style.
---
### Object-oriented Programming
---?image=assets/ITER_model.jpg
---
### Principles of OOP

- "Objects" incorporate both data and procedures.
- Data is "encapsulated" and not modified directly.
- Operations are performed on data through simplified interfaces.
- Objects may be derived from other objects through inheritance or composition.
---
### Perceived benefits

- Modularity
- Code reuse
- Protection of data from modification
- Abstracted interfaces (polymorphism)
- Natural way of thinking about the world
---
### Example

``` java
class TwentyFour {
    // Class definition for the Range object.
    public static class Range {
        private int start;
        private int finish;
        private int[] range;

        // Constructor for the Range object.
        public Range(int s, int f) {
            start = s;
            finish = f;
            range = new int[(finish + 1) - start];
            
            for (int i = 0; i < (finish + 1) - start; i++) {
                range[i] = start + i; 
            }
        }

        // toString method for the Range object.
        public String toString() {
            String output = "";
            for (int i = 0; i < range.length; i++) {
                output += range[i] + "\n";
            }
            return output; 
        }
    }

    // The main method.
    public static void main(String[] args) {
        int begin = 1, end = 24;

        Range r = new Range(begin, end);
        System.out.print(r);
    }
}
```
---
### Object-oriented Programming Languages

- Class: Simula 67, Smalltalk, C++, Objective-C, Python, Java, C#
- Prototype: Self, Lua, JavaScript, Rebol 
---
### Functional Programming
---
### What is functional programming? 

- Lambdas?
- No side effects? 
- Immutable data?
- Recursion?
- Higher-order functions?
- Closures?
- Currying?
- Monads? 
---?image=assets/760px-Selznick_Kimball_Young.jpg
---?image=assets/680px-Ford_assembly_line_-_1913.jpg
---
### Function Composition

Lisp:
``` lisp
(baz (bar (foo x)))
```

Erlang:
``` erlang
baz(bar(foo(X))).
```

Scala:
``` scala
x.foo().bar().baz()
```

Unix:
``` shell
foo x | bar | baz
```
---
### Principles of Functional Programming

- No side effects
- Immutable data
- Function composition
---
### How does it work?

- Data structures as parameters and return values
- Recursion vs. iteration
- Higher-order functions vs. iteration
- Pattern-matching vs. IF statements
- Small functions forming larger functions 
- Save side effects for last
---
### Perceived Benefits

- Less verbose 
- Easier to prove correct
- Fewer bugs
- Easier to make parallel or concurrent
---
### Functional Programming Languages

- Lisp, Scheme, Clojure, Racket
- Standard ML, OCaml, F#, Scala, Elm
- Hope, Miranda, Haskell
- Erlang, Elixir
- Matlab/Octave, R
---
### Recursion

Iteration:
``` python
for n in range(1,25):
    print(n)
```

Recursion:
``` python
def count(s,f):
    if s <= f:
        print(s)
        count(s+1,f)

count(1,24)
```
---
### Lisp

``` lisp
(defun range (first last)
  (if (<= first last)
    (progn
      (format t "~a~%" first)
      (range (+ 1 first) last))))

(range 1 24)
```
---
### Lisp - List + Delayed Side Effects

``` lisp
(defun range (first last)
  (if (<= first last)
      (cons first (range (+ 1 first) last))))

(format t "~{~a~%~}" (range 1 24))
```
---
### Objective Caml - Pattern Matching

``` ocaml
open Printf;;

let rec range s f =
  match s == f with
  | true -> [f]
  | _ -> s :: range (s + 1) f;; 

let numlist = range 1 24;;
let () = List.iter (printf "%d\n") numlist
```
---
### Erlang - Case Expression

``` erlang
range(S,F) ->
    case S == F of
      true -> [F];
      _ -> [S|range(S+1,F)]
    end.

main([]) ->
    [io:format("~w~n", [E]) || E <- range(1,24)].
```
---
### Erlang - Pattern Matching 

``` erlang
range(F,F) -> [F];
range(S,F) -> [S|range(S+1,F)]. 

main([]) ->
    [io:format("~w~n", [E]) || E <- range(1,24)].
```
---
### Erlang - Tail Recursion

``` erlang
range(S,F) -> range(S,F,[]).

range(S,F,Acc) when S > F -> Acc;
range(S,F,Acc) -> range(S,F-1,[F|Acc]). 

main([]) ->
    [io:format("~w~n", [E]) || E <- range(1,24)].
```
---
### Higher-order Functions

- **map:** apply function to each element
```
f(x) -> 2*x:

[1,2,3,4] -> [2,4,6,8]
```
- **filter:** remove matching elements
```
f(x) -> x, x % 2 == 0:

[1,2,3,4] -> [1,3]
```
- **reduce:** 
```
f(x,y) -> x*y:

[1,2,3,4] -> [10]
```
---
### Haskell - Higher-order Functions

``` haskell
main = do
    sequence (map print [1..24])
```
``` haskell
main = do
    mapM print [1..24]
```
---
### Scala - Higher-order Functions

``` scala
1.to(24).map(println)
```

``` scala
1 to 24 map println
```
---
### Pyret - Higher-order Functions

``` python
map(print, range(1,25))
```

``` python
range(1,25).map(print)
```
---
### Logic Programming
---?image=assets/Leonard_Nimoy_Spock_1967.jpg
---
### Anatomy of a Function

Function (Erlang):
``` erlang
max(X,Y) when X >= Y -> X;
max(X,Y) when X < Y -> Y.
```
---
### Functions vs. Relations

Function (Erlang):
``` erlang
max(X,Y) when X >= Y -> X;
max(X,Y) when X < Y -> Y.
```

Relation (Prolog):
``` prolog
max(X,Y,X) :- X >= Y.
max(X,Y,Y) :- X < Y.
```
---
### Facts and Rules

``` prolog
vulcan(surak).
vulcan(tpau).
vulcan(sarek).

mortal(X) :- vulcan(X).
```
---
### Backtracking

``` prolog
?- vulcan(Y).
Y = surak ;
Y = tpau ;
Y = sarek.

```
---
### Logical Inference

``` prolog
?- mortal(Z).

```
---
### Logical Inference

``` prolog
?- mortal(Z).
Z = surak ;
Z = tpau ;
Z = sarek.

```
---
### Prolog - Recursion

``` prolog
:- initialization main.

range(F,F,Tail) :- !, Tail = [F].
range(S,F,[S|Tail]) :- N is S+1, range(N,F,Tail).

main :-
    range(1,24,Range),
    maplist(writeln,Range),
    halt. 
```
---
### Prolog - Higher-order Relations

``` prolog
:- initialization main.

main :-
    numlist(1,24,Range),
    maplist(writeln,Range),
    halt.
```
---
### Logic Programming Languages

- Prolog, Datalog, Mercury, Logtalk
- Planner, CycL, Oz, Gödel, Twelf
---
### Summary

- **Procedural:** scope
- **Object-oriented:** encapsulation
- **Functional:** function composition
- **Logic:** logical relations
---
### Questions?
