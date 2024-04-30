---
tags:
  - ✅
published: true
sr-due: 2025-12-12
sr-interval: 613
sr-ease: 310
---
⬅️ [[Structure and Interpretation of Computer Programs]]

## 1A: Overview and Introduction to Lisp
- **imperative** (how to do something) vs **declarative** (what you are looking for) 🤔

- procedures direct the processes
- Lisp descriptions of processes, called _procedures_ can themselves be manipulated as Lisp data.
- data is stuff that we want to manipulate and procedures are descriptions of the rules for manipulating data

How does the language form complex ideas?
- primitives (the simplest entities of a language)
- means of combinations (building compound elements from simple elements)
- means of abstraction (naming and manipulating compound elements)

- you type in an **expression** and the computers **evaluates** it.
- **combination** is **operator** (+, -, etc) with **operands**
- `lisp` uses **prefix notation** (the operator comes first) (as opposed to infix)
- parentheses in lisp are precise (you cannot leave them out not can you use them for arbitrary grouping)
- parens signal a combination (operator + operands)
- read-eval-print loop (read an expression from the terminal, evaluate the expression and print the result)
- syntax = the various kinds of expression each with its associated evaluation rule

### Procedure definition
```lisp
(define (square x) (* x x*))
```

## Data structures
- two types: atom and list
- and atom is either a number or a symbol
- a list is a sequence of atoms or lists
- we name things with `define`: `(define size 2)`
- _environment_: provides a context in which evaluation takes place aka the memory that keeps track of the name-object pairs
- `define` is lisp's simplest way of abstraction

## Black-box abstraction
- primitive objects
	- primitive procedures
	- primitive data
- means of combination
	- procedure combination
	- construction of compound data
- means of abstraction
	- procedure definition
	- simple data abstraction
- capturing common patterns
	- high-order procedures
	- data as procedures


### Applicative-order evaluation vs normal-order evaluation
- in applicative order execution (like regular Scheme), all procedure arguments are evaluated before applying the procedure. 
- In normal order execution, procedure arguments are evaluated after applying the procedure, and then only if the result is needed to complete the evaluation of the procedure

### Predicate
- A predicate is a function/procedure/method that returns a boolean (true/false) value based on its inputs.
- usually ends with `?`

## Lambda
- lambda stands for "make a procedure"
```lisp
(define (x) 100) 
; ^ just syntactic sugar
; and the same as:
(define x          ; define the variable named x
        (lambda () ; as a anoymous function with zero arguments
          100))    ; that returns 100


(define (square x) (* x x))

; same as
(define square (lambda (x) (* x x)))
```

- 💡 **having defined square we can now use it as a primitive!**
- the things that you construct have all the same powers as the primitives

```lisp
(define a (+ 5 5))

(define (d) (*5 5) )

a ; 10
d ; compound-procedure
(d) ; 25
(a) ; error
```

## Case analysis
```lisp
(define (abs x)
	; with only one operand, the - negates the value
  (cond ((< x 0) (- x))
        ((= x 0) 0)
        ((> x 0) x)))

; same as
(define (abs-if x)
  (if (< x 0)
      (- x)
      x))
```

What's the difference between defining a variable and a procedure?
```lisp
(define A (* 5 5))
(define (D) (* 5 5))

A => 25
D => Compound procedure D
(A) => error
(D) => 25
```


- "Lisp descriptions of processes, called procedures, can themselves be represented and manipulated as Lisp data." 💡 Translated to JS, functions are first-class citizens?
- the name identifies a variable whose value is the object.
- `define` is our language’s simplest means of abstraction, for it allows us to use simple names to refer to the results of compound operations
- the **global environment** is in charge of the memory for these name-object pairs
- recursion is a very powerful technique for dealing with hierarchical, treelike objects. 
- the “percolate values upward” form of the evaluation rule is an example of a general kind of process known as tree accumulation.
- the key point to notice is the role of the environment in determining the meaning of the symbols in expressions (e.g. what does `+` do?)
- `define` is a special form (special forms have their own rules for evaluation)
- Compound procedures are used in exactly the same way as primitive procedures.

💡 So the left-most operator is always the `car` and the rest is the `cdr`

### The substitution model vs app
- fully expand and then reduce (normal-order evaluation)
- the interpreter first evaluates the operator and operands and then applies the resulting procedure to the resulting arguments (applicative-order evaluation)

### Case analysis
- predicate follow by a consequent expression
- if none is true then `undefined` is returned
```lisp
(define (abs x) (cond ((> x 0) x)
                      ((= x 0) 0)
                      ((< x 0) (- x))))
```
- **predicate**: used for procedures that return true or false, as well as for expressions that evaluate to true or false. 

same as:
```lisp
(define (abs x)
  (cond ((< x 0) (- x))
        (else x)))
```

and:
```lisp
(define (abs x)
  (if (< x 0)
      (- x)
      x))
```

### Square Roots by Newton’s Method
- Procedures are much like ordinary mathematical function. They specify a value that is determined by one or more parameters.
- n mathematics we are usually concerned with **declarative** (what is) descriptions, whereas in computer science we are usually concerned with **imperative** (how to) descriptions.

```lisp
(define (sqrt x)
  (sqrt-iter 1.0 x))

(define (sqrt-iter guess x)
  (if (good-enough? guess x)
      guess
      (sqrt-iter (improve guess x) x)))

(define (good-enough? guess x)
  (< (abs (- (square guess) x)) 0.001))

(define (improve guess x)
  (average guess (/ x guess)))


; improved version nested inside a block structure
(define (sqrt x)
	
  (define (good-enough? guess)
    (< (abs (- (square guess) x)) 0.001))
	
  (define (improve guess)
    (average guess (/ x guess)))
	
  (define (sqrt-iter guess)
    (if (good-enough? guess) guess
        (sqrt-iter (improve guess))))
  (sqrt-iter 1.0))

```

### Procedures as Black-Box Abstractions
- a procedure definition should be able to suppress detail (aka procedural abstraction)
- the procedure definition **binds** its formal parameters (if a variable is not bound it's **free**)
- the set of expressions for which a binding defines a name is called the scope of that name.
- In a procedure definition, the bound variables declared as the formal parameters of the procedure have the body of the procedure as their **scope**.