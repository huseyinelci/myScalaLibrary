## "Hello World" from Scala
```scala
object Hello extends {
  def main(args: Array[String]) {
    println("hello")
  }
}
```
#### Difference between Val and Var
```scala
// Val : Makes a variable immutable. No value is assigned later (as final in JAVA)
// Var : Makes a variable mutable. Value is assigned later

// Wrong Code Syntax
x = 6 // It must use var
println(x)

// Rigth Code Syntax
val y = 12
println(y)

// Option Rigth Code Syntax. It is not necessary to assign a data type.
val y:Int = 12
println(y)

```

#### Decrease and Increase
```scala
val x = 1 // ; yok 

def increase(i: Int) ={
  i + 1
}

def decrease(i: Int): Int =  i - 1

val y = increase(x)
val z = decrease(x)
println(y)
println(z)
  }
}
```
```
Output:
2
0
```

```scala
val s = "Hello, world"
// Herşey object
val length = s.length // 12

val concatenate = "Hello" + " world" // string birleştirme
```

```scala
/**
* h
* e
* l
* l
* o
*/
"hello".foreach(println)
for( c <- "hello") println(c)
```
```scala
// zincirlemeli fonksiyon çalıştırma
val c = "scala".drop(2) // ala
val t = "scala".take(2) // sc
val f = "scala".drop(2).take(2) // al
val cap = "scala".drop(2).take(2).capitalize // Al
```
```scala
// çoklu satırlı string
val foo = """This is
          a multiline
          String"""
println(foo) 


val speech = """Four score and
                #seven years ago""".stripMargin('#')
println(foo)
// Four score and
// seven years ago
```
```scala
"hello world".split(" ").foreach(println)
// hello
// world
```
String içine değişken koyma
```scala
val age = 1
println(s"Age next year: ${age + 1}") // Age next year: 2


val name = "muhammed".capitalize
val age = 2
val weight = 66.77
println(f"$name is $age years old, and weighs $weight%.2f pounds.")

//Muhammed is 2 years old, and weighs 66,77 pounds.


val name = "Muhammed"
val age = 12

println("%s is %d years old".format(name, age)) // Muhammed is 12 years old
```
// Karakter karakter
```scala
val upper = "hello, world".map(p => p.toUpper)
val upper2 = "hello, world".map(_.toUpper)
```
## Match
```scala
// Bunun yerine
def ayIsimleri(n: Int): String = {
  if(n==1) "Ocak"
  else if(n==2) "Şubat"
  else "Bilinmiyor"
}

// Bu 
def ayIsimleri(n: Int): String = n match {
  case 1 => "Ocak"
  case 2 => "Şubat"
  case _ => "Bilinmiyor" // default
}
```
```scala
// Başka bir örnek
def daysInMonth(n: Int): Int = n match {
  case 1 | 3 | 5 | 7 | 8 | 10 | 12 => 31
  case 4 | 6 | 9 | 11 => 30
  case 2 => 28
  case _ => 0 // default
}
println(daysInMonth(6)) // 30
```
```scala
def watIsIt(birsey: Any): String = birsey match {
  case 1 => "1 numara"
  case "hello" => "selamlama"
  case List(_, _) => "2 elamanlı bir liste"
  case List(_, _, _) => "3 elamanlı bir liste"
}
println(watIsIt(List(2, 3)))
```
```scala
def watIsIt(birsey: Any): String = birsey match {
  case n: Int => "Sayı "+ n
  case s: String => "String "+ s
  case _ => "Başka bir şey"
}
println(watIsIt("Kemal"))
```
## Try Catch
```scala
def parseInt(s: String): Int = try {
  s.toInt
} catch {
  case e: NumberFormatException => 0
}
println(parseInt("kema")) // 0


def parseInt(s: String): Option[Int] = try {
  Some(s.toInt)
} catch {
  case e: NumberFormatException => None
}
println(parseInt("0")) // Some(0)
```


Call by Value - Call by Name
```scala
// call by value
def constOne(x:Int, loop) = 1
def constOne(x:Int, y:Int) = 1

// call by name
def constOne(x:Int, loop) = 1
def constOne(x:Int, y: => Int) = 1
```
Regex
```scala
// Regex tanımlama
val numPattern = "[0-9]+".r

import scala.util.matching.Regex
val numPattern = new Regex("[0-9]+")



val numPattern = "[0-9]+".r
val address = "123 Main Street Suite 101"
val match1 = numPattern.findFirstIn(address) // Some(123)



val numPattern = "[0-9]+".r
val address = "123 Main Street Suite 101"
val matches = numPattern.findAllIn(address)
matches.foreach(println) // 123, 101



val regex = "[0-9]".r
val newAddress = regex.replaceAllIn("123 Main Street", "x") // xxx Main Street



val result = "123".replaceFirst("[0-9]", "x") // x23
```
Fonksiyonel programlama
```scala

def f(y: Int) = y +1

// değişkene fonksiyon atandı
val result = {
  val x = f(3)
  x
} // result = 4

```
## Implicit
```scala
// String'i (2'lik taban) Int yapar
implicit class StringToInt(s: String) {
  def toInt(radix: Int) = Integer.parseInt(s, radix)
}
println("101".toInt(2))

```
```scala
// Değişken tanımlama
val a = 1d
val b = 1.0 : Double
val c = 0: Byte

println(b)
```
```scala
// Artırma (Increment) - Azaltma (Decrement)
var a = 1
a+=1

println(a)
```
## Döngüler
```scala
for (i:Int <- 1 to 10)
  println(i) // [1, 10]
  
  
for (i:Int <- 1 until 10)
  println(i) // [1, 9]
  
  
for(i: Int <- List(1, 2, 3)) println(i) // [1, 3]
```

## List
```scala
// Liste birleştirme operatörü ':::'
val oneTwo = List(1, 2)
val threeFour = List(3, 4)
val oneTwoThreeFour = oneTwo ::: threeFour

println(oneTwoThreeFour)


// Başa eleman ekler  '::'
val twoThree = List(2, 3)
val oneTwoThree = 5 :: twoThree
println(oneTwoThree) // List(5, 2, 3) 


val oneTwoThree = 1 :: 2 :: 3 :: Nil
println(oneTwoThree) // List(1, 2, 3)

// Liste elaman alma
val list = List("Yasin", "Kemal", "Ahmet")
println(list(1)) // Kemal


// İlk 1 eleman olmadan
val list = List("Yasin", "Kemal", "Ahmet")
println(list.drop(1)) // List(Kemal, Ahmet)


// Filtreleme
val list = List("hakan", "hak", "h")
println(list.filter(_.length == 3))      // List(hak)
println(list.filter(s => s.length == 3)) // List(hak)

```
## Tuple
```scala
// Int ve String veriyi değiştirilemez şekilde List gibi saklar

val pair = (99, "Luftballons")
println(pair._1)
println(pair._2)
```
## Set
```scala
// Değiştirilebilir Set

import scala.collection.mutable
val movieSet = mutable.Set("Hitch", "Poltergeist")
movieSet += "Shrek"
println(movieSet)
```
## Map
```scala
// Mutable Map

import scala.collection.mutable

val treasureMap = mutable.Map[Int, String]()
treasureMap += (1 -> "Go to island.")
treasureMap += (2 -> "Find big X on ground.")
treasureMap += (3 -> "Dig.")
println(map(1))


val map = mutable.Map[Int, String](
  1 -> "Naber",
  2 -> "hakan"
)
println(map(1))
```

## Class ve Object
### Class
```scala
// Class tanımlama

class ChecksumAccumulator {
  var sum = 0
}
val acc = new ChecksumAccumulator
```
```scala
// Private 
class ChecksumAccumulator {
  private var sum = 0
}

val acc = new ChecksumAccumulator
println(acc.sum) // Hata
```

Yemek Tarifi Class'ı
```scala
// YemekTarifi.scala

class YemekTarifi(val malzemeler: List[String], val tarifler: List[String]) {
  println("Malzemeler: "+malzemeler)
  println("Tarifler: "+tarifler)
}
```
```scala
// Hello.scala

object Hello extends {
  def main(args: Array[String]) {
    val yemekTarifi = new YemekTarifi(
      List("yumurta", "yağ", "tuz"),
      List("Yağı kızdırıp yumurtaları içine kır")
    )
  }
}
```
Constructor
```scala
// constructor
class YemekTarifi(val malzemeler: List[String] = List.empty, 
                  val tarifler: List[String]= List.empty) {
  println("Malzemeler: "+malzemeler)
  println("Tarifler: "+tarifler)
}
```
```scala
class Cookbook(val yemekTarifleri: Map[String, YemekTarifi]) {
  println("Yemek Tarifleri: "+yemekTarifleri)

  def this() = this(Map.empty) // constructor
}
```

### Object
```scala
/**
 * Aynı isimde Class ve Object tanımladığında birbirinin arkadaşı olur
 * Aralarında private değişkenleri paylaşabilirler
 * Java'da olan static Scala'da yoktur, Object static fonk. yerine kullanılabilir
 */
 
// Math.scala - Object
object Math {
  private val cache = Map[String, Int]()
  def topla(a: Int, b: Int): Int = {
    a+b
  }
}


// Hello.scala - Object
import Math.topla

object Hello extends {
  def main(args: Array[String]) {
    println(topla(2, 4)) // Object static fonk. gibi kullanıldı
  }
}
```

Apply - Unapply metodlarına çalış
```scala
```

```scala
```

```scala
```

```scala
```

```scala
```

```scala
```

```scala
```
