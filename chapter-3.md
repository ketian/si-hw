# Chapter 3: Working with Arrays

1. suppose `n = 20`:

  ```scala
  val n = 20
  val a = Seq.fill(n)(scala.util.Random.nextInt(n)).toArray
  ```

2. suppose `a` is an `Array`:

  ```scala
  for (i <- 0 until (a.length-1, 2)) { val p = a(i); a(i) = a(i+1); a(i+1) = p; }
  ```

3. suppose `a` is an `Array`:

  ```scala
  // dull & ugly
  (for (i <- 0 until a.length) yield 
    if (a.length%2 == 1 && i == a.length-1) a(i) 
    else if (i%2 == 0) a(i+1) 
    else a(i-1)).toArray
  // bling bling
  a.grouped(2).flatMap(_.reverse).toArray
  ```

4. suppose `a` is an `Array`:

  ```scala
  a.filter(_ > 0) ++ a.filter(_ <= 0)
  ```

5. suppose `a` is an `Array[Double]`:

  ```scala
  a.sum / a.length
  ```

6. suppose `a` is an `Array[Int]` or `ArrayBuffer[Int]`:

  ```scala
  // it seems that there is an error in page 36
  // `sortWith` (not `sorted`) should be used if you want to pass a comparison function
  // `sorted` takes implicit math.Ordering
  val ars = a.sortWith(_ > _)
  // also, notice that those sort methods won't touch `a` itself
  // so that `scala.util.Sorting._` should be used here, like:
  import scala.util.Sorting.quickSort
  quickSort[Int](a)(Ordering[Int].reverse)
  // `quickSort` cannot be applied to an `ArrayBuffer`
  // if you want to sort an `ArrayBuffer` in place, 
  // you might need to: 1. sort & generate a new ArrayBuffer, 2. reassign
  ```

7. suppose `a` is an `Array`:

  ```scala
  a.distinct
  ```

8. suppose `a` is an `ArrayBuffer`:

  ```scala
  val indices = a.zipWithIndex.filter(_._1 < 0).map(_._2)
  for (j <- indices.drop(1).reverse) a.remove(j)
  ```

9. code:

  ```scala
  import java.util.TimeZone.getAvailableIDs
  // `sorted` might not be neccessary
  val ans = getAvailableIDs.filter(_ startsWith "America/").map(_ drop 8).sorted
  ```

10. code:

  ```scala
  // enable auto-transfer from `java.util.List` to `scala.collection.mutable.Buffer`
  import scala.collection.JavaConversions.asScalaBuffer
  import scala.collection.mutable.Buffer
  import java.awt.datatransfer._
  val flavors = SystemFlavorMap.getDefaultFlavorMap().asInstanceOf[SystemFlavorMap]
  val buffer: Buffer[String] = flavors.getNativesForFlavor(DataFlavor.imageFlavor)
  ```

----

2016-02-18
