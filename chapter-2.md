# Chapter 2: Control Structures and Functions

1. `signum`:

  ```scala
def signum(x: Int): Int = if (x>0) 1 else if (x<0) -1 else 0
  ```

2. no value, `Unit()`

3. `x` should be a `var` with type `Unit()` (e.g. `var x = ()`)

4. Code:

  ```scala
// no loop
(1 to 10).map((i: Int) => println(i))
// scala for loop
for (i <- 1 to 10) println(i)
  ```

5. `countdown`:

  ```scala
def countdown(n: Int): Unit = (n.to(0, -1)).map((i: Int) => println(i))
  ```

6. `for` loop to compute product:

  ```scala
var x = 1
for (i <- "Hello") x *= i
x
  ```

7. No `for` loop:

  ```scala
"Hello".foldLeft(1)(_*_)
  ```

8. `product`:

  ```scala
// no recursion
def product(s: String): Int = s.foldLeft(1)(_*_)
// recursion
def product(s: String): Int = if (s.isEmpty) 1 else s.head * product(s.tail)
// tail recursion
def product(s: String): Int = {
  def rec(s: String, ans: Int): Int = 
    if (s.isEmpty) ans
    else rec(s.tail, s.head * ans)
  rec(s, 1)
}
  ```

9. ^ look upside

10. Code:

  ```scala
def square(x: Int): Int = x*x
def pow(x: Int, n: Int): Int = 
  if (n < 0) pow(x, -n)
  else if (n == 0) 1
  else if (n % 2 == 0) square(pow(x, n/2))
  else x*pow(x, n-1)
  ```

----

2016-02-17
