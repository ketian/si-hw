# Chapter 5: Classes

1. imporved `Counter`:

  ```scala
  class Counter {
    private var value = 0
    def increment() { if (value < Int.MaxValue) value += 1 }
  }
  ```

2. `BankAccount`:

  ```scala
  class BankAccount(private var money: Int = 0) {
    def balance = money
    def deposit(x: Int) { money += x }
    def withdraw(x: Int) =
      if (money >= x) {
        money -= x
        x
      } else 0
  }
  ```

3. `Time`:

  ```scala
  class Time(val hours: Int, val minutes: Int) {
    require(hours >= 0 && hours <= 23, "hours should between 0 and 23")
    require(minutes >= 0 && minutes <= 59, "minutes should between 0 and 59")
    def before(other: Time) =
      (other.hours > hours) || (other.hours == hours && other.minutes > minutes)
  }
  ```

4. `Time2`:

  ```scala
  class Time2(val hours: Int, val minutes: Int) {
    require(hours >= 0 && hours <= 23, "hours should between 0 and 23")
    require(minutes >= 0 && minutes <= 59, "minutes should between 0 and 59")
    private val time = hours * 60 + minutes
    def before(other: Time2) = time < other.time
  }
  ```

5. `Student`:

  ```Scala
  import scala.reflect.BeanProperty
  class Student(@BeanProperty var name: String, @BeanProperty var id: Long) {}
  ```
  `getter`s and `setter`s are generated and can be called in Scala. But they shoudn't be used in Scala.

6. improved `Person`:

  ```Scala
  class Person {
    var age = 0
    def this(age: Int) { this(); this.age = if (age < 0) 0 else age }
  }
  ```

7. `Person2`:

  ```Scala
  // there is no need to save `fullName` as a field,
  // and since `fullName` is not used in any method,
  // `fullName` will be a regular parameter
  class Person2(fullName: String) {
    val firstName = fullName.split(' ')(0)
    val lastName = fullName.split(' ')(1)
  }
  ```

8. `Car`:

  ```Scala
  class Car(val manufacturer: String, val modelName: String, val modelYear: Int = -1) {
    var licensePlate = ""
    def this(manufacturer: String, modelName: String, licensePlate: String) {
      this(manufacturer, modelName)
      this.licensePlate = licensePlate
    }
    def this(manufacture: String, modelName: String, modelYear: Int, licensePlate: String) {
      this(manufacture, modelName, modelYear)
      this.licensePlate = licensePlate
    }
  }
  
  val car0 = new Car("BMW", "M6")
  val car1 = new Car("Benz", "S65 AMG", 2015)
  val car2 = new Car("Porsche", "911 GTS", "?")
  val car3 = new Car("Audi", "A7", 2016, "???")
  ```

9. Much shorter. `;p`

10. rewrited `Employee`:

  ```scala
  class Employee {
    private var _name = "John Q. Public"
    var salary = 0.0
    def this(name: String, salary: Double) { this(); this._name = name; this.salary = salary }
    def name = _name
  }
  ```
  The one on the book is preferred.