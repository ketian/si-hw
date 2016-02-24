# Chapter 6: Objects

1. `Conversions`:

  ```scala
  object Conversions {
    def inchesToCentimeters(x: Double) = 2.54 * x
    def gallonsToLiters(x: Double) = 3.785411784 * x  // US gallon
    def milesToKilometers(x: Double) = 1.609344 * x
  }
  ```

2. `UnitConversion` and other implemented objects:

  ```scala
  abstract class UnitConversion {
    def apply(x: Double): Double
  }
  
  object InchesToCentimeters extends UnitConversion {
    def apply(x: Double) = 2.54 * x
  }
  
  object GallonsToLiters extends UnitConversion {
    def apply(x: Double) = 3.785411784 * x
  }
  
  object MilesToKilometers extends UnitConversion {
    def apply(x: Double) = 1.609344 * x
  }
  ```

3. `Origin`:

  ```scala
  object Origin extends java.awt.Point {}
  ```
  Notice that `java.awt.Point` is not an abstract class and has implemented several methods that can change the coordinates, which means users can easily destroy this object by, say, `Origin.setLocation(1, 1)`. In order to prevent such things, we have to override all those methods, like: `override def setLocation(x: Int, y: Int) {}`. To do things like this is quit tedious and stupid.

4. `Point` with its companion object:

  ```scala
  class Point(val x: Double, val y: Double) {
    def this() = this(0, 0)
    override def toString = "(" + x + ", " + y + ")"
  }
  
  object Point {
    def apply(x: Double, y: Double) = new Point(x, y)
  }
  
  val p = Point(3, 4)
  ```

5. `Reverse`:

  ```scala
  object Reverse extends App {
    println(args.reverse.mkString(" "))
  }
  ```

6. `PlayingCardSuit`:

  ```scala
  object PlayingCardSuit extends Enumeration {
    val hearts = Value("♥")
    val tiles = Value("♦")
    val clovers = Value("♣")
    val pikes = Value("♠")
  }
  ```

7. `checkHearts`:

  ```scala
  def checkHearts(x: PlayingCardSuit.Value) = x == PlayingCardSuit.hearts
  ```

8. So-called "Corners of RGB Color Cube":

  ```scala
  object RGBColor extends Enumeration {
    val black   = Value(0x000000)
    val blue    = Value(0x0000FF)
    val green   = Value(0x00FF00)
    val cyan    = Value(0x00FFFF)
    val red     = Value(0xFF0000)
    val magenta = Value(0xFF00FF)
    val yellow  = Value(0xFFFF00)
    val white   = Value(0xFFFFFF)
  }
  ```
  Tips: if you are intereseted in color space, see [Organizing Color](http://viz.aset.psu.edu/gho/sem_notes/color_2d/html/primary_systems.html) for more information.

----

2016-02-24