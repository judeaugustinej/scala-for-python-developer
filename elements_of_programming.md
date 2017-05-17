### REPL - Read-Eval-Print-Loop
* Installing standard scala
```
$ scala
scala >
```

* Using scala-build-tool
```
$ sbt
> console
scala >
```
or
```
$ sbt console
scala >
```
* Basic Maths operation(+,-,/,%)
```
scala> // Single line comment

scala> // Add two number

scala> 5 + 6
res5: Int = 11

scala> // subtract two number

scala> 6 -2
res6: Int = 4

scala> 2 - 4
res7: Int = -2

scala> // multiply two numbers

scala> 7 * 4
res8: Int = 28

scala> // divide

scala> 11/2
res9: Int = 5

scala> 11%2
res10: Int = 1

```
### Evaluation

* Take the leftmost operator
* Evaluate its operands (left before right)
* Apply the operator to operands
```
(2 * pi) * radius
(2 * 3.14159) * radius
6.24318 * radius
6.24318 * 10
62.4318
```
### Definitions
```
scala> def age = 24
age: Int

scala> age
res11: Int = 24

```
* Definitions with parameters
```
scala> def square(x: Double) = x * x
square: (x: Double)Double

scala> square(2)
res12: Double = 4.0

scala> square(5 + 4)
res13: Double = 81.0

scala> square(square(4))
res14: Double = 256.0

scala> def sumOfSquares(x: Double, y: Double) = square(x) + square(y)
sumOfSquares: (x: Double, y: Double)Double

scala> sumOfSquares(5, 3)
res15: Double = 34.0

```
* Primitive types are as in Java, but are written capitalized
```
Int  32-bit integers
Double 64-bit floating point numbers
Boolean boolean values true and false
```
### Evaluation of Function applications
* Evaluate all function arguments, from left to right
* Replace the function application by function's right-hand
side, and at the same time,
* Replace the formal parameters of the function by actual
arguments
```
// substitution model -- Call-by-value
// evaluate argument first
sumOfSquare(3, 2+2)
sumOfSquare(3, 4)
square(3) + square(4)
3 * 3 + square(4)
9 + square(4)
9 + 4*4
25
// another evaluation strategy -- Call-by-name
// body get evaluate
sumOfSquares(3, 2+2)
square(3) + square(2+2)
3 * 3 + square(2+2)
9 + square(2+2)
9 + (2+2) * (2+2)
9 + 4 * 4
25
```
* CBV - It evaluates every function argument only once.
* CBN - Function arguments is not evaluated if the corresponding parameter is
unused in the evaluation of the function body.
### CBN v/s CBV
```
def test(x: Int, y:Int) = x * x
```
* test(2, 3)
```
// CBN
2 * 3
6
// CBV
test
```
* test(3+4, 8)
```
// CBN
(3+4) * 8
7 * 8
56
// CBV
test(7, 8)
7 * 8
56
```
* test(7, 2*4)
```
// CBN
7 * (2*4)
7 * 8
56
//CBV
test(7, 8)
7 * 8
56
```
* test(3+4, 2*4)
```
// CBN
(3+4) * (2*4)
7 * 8
56
// CBV
test(7, 2*4)
test(7, 8)
7 * 8
56
```
### Termination for CBV and CBN
* If CBV evaluate to e terminates, then CBN also evaluation 
terminates too
* The other direction is not true
* Example where CBN terminates but CBV does'nt
```
```
