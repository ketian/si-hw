#Chapter 1: The Basics

1. `%`, `&`, `*`, `+`, `-`, `/`, `>`, `>=`, `>>`, `>>>`, `^`, `asInstanceOf`, `isInstanceOf`, `toByte`, `toChar`, `toDouble`, `toFloat`, `toInt`, `toLong`, `toShort`, `toString`, `unary_+`, `unary_-`, `unary_~`, `|`
2. 
  ```scala 
math.sqrt(3)
math.sqrt(res0)
3 - res1
  ```
3. `val` (try `res0 = 1`)
4. `"crazy" * 3` generates `"crazycrazycrazy"` which can be found in: [Scaladoc-String](http://www.scala-lang.org/api/current/index.html?&_ga=1.138007600.1611065700.1455630876#scala.collection.immutable.StringOps)
5. `10 max 2` == `10.max(2)`, method `max` is defined in `RichInt` according to [Scaladoc-Int](http://www.scala-lang.org/api/current/index.html?&_ga=1.138007600.1611065700.1455630876#scala.Int)
6. `BigInt(1) << 1024`
7. `import BigInt.probablePrime`, `import scala.util.Random`
8. `BigInt.probablePrime(128, scala.util.Random) toString 36`
9. `"abc".head`, `"abc".last`
10. 
  ```scala
def take(n: Int): String -> Selects first n elements.
def drop(n: Int): WrappedString -> Selects all elements except first n ones.
def takeRight(n: Int): String -> Selects last n elements.
def dropRight(n: Int): WrappedString -> Selects all elements except last n ones.
  ```
Compare to `substring`, `take` and `drop` are native scala methods, which means that when those methods are called, implicit conversion from `StringOps` to `String` will not performed by method `unaugmentString` in `scala.Predef`. 
I think those methods are always prefered comparing to `substring`.

----
2016-02-16
