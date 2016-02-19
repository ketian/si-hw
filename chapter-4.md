# Chapter 4: Maps and Tuples

1. code:

  ```scala
  val a = Map("a" -> 12.8, "b" -> 5.6, "c" -> 15.2)
  // no loop
  val b = a.map((i) => (i._1, i_2 * 0.9))
  // or, with a loop
  val b = for (i <- a) yield (i._1, i._2 * 0.9)
  ```

2. count the words in `chapter-3.md`:

  ```scala
  import java.util.Scanner
  import java.io.File

  val words = new scala.collection.mutable.HashMap[String, Int]
  val in = new Scanner(new File("chapter-3.md"))
  while (in.hasNext()) {
    val word = in.next()
    if (words.contains(word)) words(word) += 1
    else words(word) = 1
  }
  words
  ```

3. ^ look upside:

  ```scala
  import java.util.Scanner
  import java.io.File

  var words = new scala.collection.immutable.HashMap[String, Int]
  val in = new Scanner(new File("chapter-3.md"))
  while (in.hasNext()) {
    val word = in.next()
    if (words.contains(word)) {
      val freq = words(word)
      words = words - word
      words = words + (word, freq + 1)
    } else words = words + (word, 1)
  }
  words
  ```

4. ^ look upside:

  ```scala
  import java.util.Scanner
  import java.io.File

  var words = new scala.collection.immutable.TreeMap[String, Int]
  val in = new Scanner(new File("chapter-3.md"))
  while (in.hasNext()) {
    val word = in.next()
    if (words.contains(word)) {
      val freq = words(word)
      words = words - word
      // `words = words + (word, freq + 1)` leads an error (type mismatch) here
      // and I have no idea why it is…
      words = words + ((word, freq + 1))
    } else words = words + ((word, 1))
  }
  words
  ```

5.  ^ look upside:

  ```scala
  import java.util.Scanner
  import java.io.File
  import scala.collection.JavaConversions.mapAsScalaMap

  val words: scala.collection.mutable.Map[String, Int] = new java.util.TreeMap[String, Int]
  val in = new Scanner(new File("chapter-3.md"))
  while (in.hasNext()) {
    val word = in.next()
    if (words.contains(word)) words(word) += 1
    else words(word) = 1
  }
  words
  ```

6. code:

  ```scala
  import java.util.Calendar._
  val days = scala.collection.mutable.LinkedHashMap("Monday" -> MONDAY,
    "Tuesday" -> TUESDAY, "Wednesday" -> WEDNESDAY,
    "Thursday" -> THURSDAY, "Friday" -> FRIDAY,
    "Saturday" -> SATURDAY, "Sunday" -> SUNDAY)
  for (i <- days) println(i)
  ```

7. code:

  ```scala
  import scala.collection.JavaConversions.propertiesAsScalaMap  val props: scala.collection.Map[String, String] = System.getProperties()
  val maxlen = props.keys.map(_.length).max
  val format = "%-" + maxlen + "s | %s\n"
  for ((k, v) <- props) printf(format, k, v)
  ```

8. code:

  ```scala
  def minmax(values: Array[Int]) = (values.min, values.max)
  ```

9. code:

  ```scala
  def lteqgt(values: Array[Int], v: Int) = (
    values.count(_ < v),
    values.count(_ == v),
    values.count(_ > v)
  )
  ```

10. `"Hello".zip("World")` generates `scala.collection.immutable.IndexedSeq[(Char, Char)] = Vector((H,W), (e,o), (l,r), (l,l), (o,d))`. 

----

2016-02-19