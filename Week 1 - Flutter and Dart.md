---
title: Week 1 - Flutter and Dart
tags: Flutter, Dart, Slide
description: View the slide with "Slide Mode".
---

---

## 1. Wellcome

### 1.1. Introduction
#### cross-platform
##### Advantages
* **Faster development**: working on a single codebase
* **Lower costs**: maintaining a single project instead of many
* **Consistency**: the same UI and functionalities on any platform.
##### Disadvantages
* **Lower performances**: A cross-platform framework might produce a slower application due to a necessary bridge required to communicate with the underlying OS
* **Slower releases**: when Google or Apple announce a major update for their OS, the main- tainers of the cross-platform solution could have the need to release an update to enable the latest features. The developers must wait for an update of the framework, which might slow down the work.

**Ex:**
![](https://i.imgur.com/tsPdeKD.png)

* **Flutter.** Created by Google, it uses Dart
* **React Native.** Created by Facebook, it is based on javascript
* **Xamarin.** Created by Microsoft, it uses the C#


### 1.2. Introduction to Dart
*Dart is a client-optimized, garbage-collected, OOP language for creating fast apps that run on any platform*
#### 1.2.1 Supported platforms
* **Stand-alone**: 
*Dart program can be executed with the Dart Virtual Machine (DVM)*

* **AOT compiled**: 
***A**head **O**f **T**ime compilation is the act of translating a high-level programming language, like Dart, into native machine code*
![](https://i.imgur.com/Kn8yqBj.png)

*Flutter SDK you can AOT compile your Dart code into a native binary for mobile, web and desktop.*

* **Web**
*With **dart2js** tool, your Dart project can be "transpiled" into fast and compact JavaScript code.*
![](https://i.imgur.com/2GckS0o.png)

#### 1.2.2 Hello world
**DartPad**: https://dartpad.dartlang.org
![](https://i.imgur.com/hwLMTaC.png)

* **main()**: entry point of the application. 
* **print()**: method outputs to the console



### 1.3. Introduction
*Flutter is an UI toolkit for building natively compiled applications for mobile, desktop and web with a single codebase*
#### 1.3.1 How does it work
* **Native app** interacts with the OS, Kotlin (or Java) for Android or Swift (or Objective-C) for iOS
![](https://i.imgur.com/JgHP3Xb.png)

* **React Native** adding a ***bridge*** in the middle that takes care of the communication with the platform
![](https://i.imgur.com/XH1Lkna.png)

* **Flutter**
![](https://i.imgur.com/4rY0iHd.png)

*Rendering engine: **Skia**
Flutter produces native ARM code for the machine
Faster than having a bridge.
A minimal Flutter app is about 4.4 MB on Android and 10.9 MB on iOS*
#### 1.3.2 Why Flutter uses Dart
Both Flutter and Dart are developed by Google

#### 1.3.3 Hello world
```java
void main() {
    runApp(MyApp());
}
class MyApp extends StatelessWidget {
    const MyApp();
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Text("Flutter app!"),
                ),
            ),
        ); 
    }
}
```
![](https://i.imgur.com/bL7CUy4.png)

---
# 2.The Dart programming language

## 2.1 Variables and data types

### Variables
```java
var value = 18;  //inference
var myName = "Alberto"; //inference
int value = 18; //explicit
String myName = "Alberto"; //explicit
dynamic value = 18;
dynamic myName = "Alberto";
```

### Initialization
*When you don’t want to initialize a variable immediately, use the late keyword*
```java
late List<String> names;
```

### Final
*A variable declared as final can be set only once*
```java
//Very popular - Automatic type deduction
final name = "Alberto";
//Generally unnecessary - With type annotation 
final String nickName = "Robert";
```

## 2.2. Data types
### 2.2.1. Number
Dart has two type of numbers:
* **int.** 64-bit at maximum
* **double.** 64-bit double-precision floating point numbers

Both **double** and **int** are subclasses of **num**

### 2.2.2. String
```java
// No differences between s and t
var s = "Double quoted";
var t = 'Single quoted';

// Interpolate an integer into a string
var age = 25;
var myAge = "I am $age years old";

// Expressions need '{' and '}' preceeded by $
var test = "${25.abs()}"
```

### 2.2.3. Enumerated types
```java
enum Fruits { Apple, Banana, Orange }

extension FruitsExtension on Fruits {
  String get vnText {
    switch (this) {
      case Fruits.Apple:
        return "Táo";
      case Fruits.Banana:
        return "Chuối";
      case Fruits.Orange:
        return "Cam";
      default:
        return "";
    }
  }
}
```

### 2.2.4. Booleans
```java
bool isOk = true;
```
### 2.2.5. Arrays
* Java
```java
// 1. Array
double[] test = new test[10];
// 2. Generic list
List<double> test = new ArrayList<>();
```
* Dart
```java
// 1. Array
// (no equivalent)
// 2. Generic list
List<double> test = new List<double>();
final myList = [-3.1, 5, 3.0, 4.4];
final value = myList[1];
final length = myList.length;
final isEmpty = myList.isEmpty;
final isNotEmpty = myList.isNotEmpty;
...
```

## 2.3. Nullable and Non-nullable types
*Starting from **Dart 2.10**, variables will be **n**on-**n**ullable **b**y **d**efault (nnbd) which means they’re not allowed to hold the **null** value.*
```java
int? value;
print("$value"); // Legal, it prints 'null'
```

## 2.4. Data type operators
### Arithmetic operators

| Symbol | Meaning | Example |
| -------| -------- | -------- |
| +      | Add two values | 2 + 3 = 5|
|-       | Subtract two values|2 - 3 = -1|
|*       | Multiply two values| 6 * 3 = 18|
|/       | Divide two values|  9 / 2 = 4.5|
| ∼/     | Integer division of two values| 9 ~/ 2 = 4|
|%       | Remainder (modulo) of an int division | 5 % 2 //1

### Relational operators
| Symbol | Meaning | Example |
| -------| -------- | -------- |
|==      | Equality test  | 2 == 6 |
|!=      | Inquality test | 2 != 6 |
|>       | Greather than  | 6 > 2 |
|<       | Smaller than   |  2 < 6 |
| >=     | Greater or equal to | 6 >= 2 |
|<=      | Smaller or equal to | 2 <= 6 |

### Type test operators
| Symbol | Meaning | Example |
| -------| -------- | -------- |
|as      | Cast a type to another  | obj as String |
|is      | True if the object has a certain type | obj is double |
|is!     | False if the object has a certain type  | obj is! int |

### Logical operators
```java
!expr //Toggles true to false and vice versa
expr1 && expr2 //Logical AND (true if both sides are true)
expr1 || expr2 //Logical OR (true if at least one is true)
```

### Bitwise and shift operators
```java
a & b     //Bitwise AND
a | b     //Bitwise OR
a ^ b     //Bitwise XOR
∼ a       //Bitwise complement
a >> b    //Right shift
a << b    //Left shift
```

## 2.5. Control flow and functions
### If statement
```java
void main() {
    final random = 13;
    if (random % 2 == 0)
        print("Got an even number");
    else
        print("Got an odd number");
}
````
### switch statement
```java
enum Status { Ready, Paused, Terminated }
void main() {
    final status = Status.Paused;
    switch (status) {
        case Status.Ready:
            run();
            break;
        case Status.Paused:
            pause();
            break;
        case Status.Terminated:
            stop();
            break;
        default:
            unknown();
    } 
}
```
### for and while loops
```java
//for
for(var i = 0; i <= 10; ++i)
    print("Number $i");
    
//while
var i = 0;
while (i <= 10) {
    print("Number $i");
    ++i; 
}
```
## 2.6.  Assertions
*While writing the code you can use assertions to throw an exception 1 if the given condition evaluates to **false***

```java
// the method returns a json-encoded string
final json = getJSON();
// if length > 0 is false --> runtime exception
assert(json.length > 0, "String cannot be empty"); 
// other actions
doParse(json);
```

## 2.7.  Functions
### The basics of functions
```java
bool checkEven(int value) {
        return value % 2 == 0
}
```
### Anonymous functions
```java
void main() {
    bool Function(int) isEven = (int value) => value % 2 == 0;
    bool Function(int) isOdd = (int value) {
        return value % 2 == 1;
    }
    print(isEven(19)); //false 
    print(isOdd(19)); //true 
}
```
### Optional parameters
```java
void test({int? a, int? b}) {
    print("$a");
    print("$b");
}  
void main() {
    // Prints '2' and '-6'  
    test(a: 2, b: -6);
    // Prints '2' and '-6'  
    test(b: -6, a: 2);
}
```
```java
void test({int? a, int b = 0}) {
    print("$a");
    print("$b");
}  
void main() {
    // Prints '2' and '0'  
    test(a: 2); 
}
```
```java
void test({int a = 0, required int b}) {
    print("$a");
    print("$b");
}
```
### Positional parameters
```java
void test([int? a, int? b]) {
    print("$a");
    print("$b");
}  
void main() {
   // Prints '2' and '-6' 
   test(2, -6);
}
```
### Nested functions
```java
void testInner(int value) {
    // Nested function
    int randomValue() => Random().nextInt(10);
    // Using the nested funcion
    final number = value + randomValue();
    print("$number");
}
```

## 2.8. Using typedefs
```java
typedef VoidCallback = void Function();
typedef LoggerFunction = void Function(String msg);
```

# 3. Class
```java
class Person {
    // Instance variables String name;
    String surname;
    // Constructor
    Person(String name, String surname) {
        this.name = name;
        this.surname = surname;
    } 
}
```
``` java
persion.surname = "Dao"
       ..surname = "Dao xinh" //using the cascade operator
```
## 3.1. Libraries and visibility
```java
import 'package:fraction.dart';

// Contains a class called 'MyClass'
import 'package:libraryOne.dart';
// Also contains a class called 'MyClass' 
import 'package:libraryTwo.dart' as second;

void main() {
    // Uses MyClass from libraryOne 
    var one = MyClass();
    //Uses MyClass from libraryTwo.
    var two = second.MyClass();
}
```
*You can selectively import or exclude types using the **show** and **hide** keywords:*
```java
//Imports only MyClass and discards all the rest.
import 'package:libraryOne.dart' show MyClass; 
//Imports everything except MyClass.
import 'package:libraryTwo.dart' hide MyClass;
```
Dart don't have **public**, **protected** and **private** keywords by default. Every member is public by default and **underscore** (_) which it private to its library
```java
// === File: test.dart ===
class Test {
    String nickname = "";
    String _realName = "";
}

// === File: main.dart ===
import 'package:test.dart';
void main() {
    final obj = Test();
    // OK
    var name = obj.nickname; 
    // ERROR, doesn't compile var real = obj._realName;
}
```
Private class and private function
```java
class _UsersHelper {
    String _nickname(){}
}
```

## 3.2. Constructors
```java
final myObject = new MyClass();
//the keyword new can be omitted
final myObject = MyClass();
```
``` java
class Fraction {
    late int _numerator;
    late int _denominator;
    Fraction(int numerator, int denominator) {
        _numerator = numerator;
        _denominator = denominator;
    } 
}
```
#### Named constructors
```java
class Fraction {
    int _numerator;
    int _denominator;
    Fraction(this._numerator, this._denominator);
    // denominator cannot be 0 because 0/0 is not defined!
    Fraction.zero() :
        _numerator = 0,
        _denominator = 1;
}

// "Traditional" initialization 
final fraction1 = Fraction(0, 1);
// Same thing but with a named constructor
final fraction2 = Fraction.zero();
```

#### Factory constructors
The ***factory*** keyword returns an instance of the given class that’s not necessarily a new one. It can be useful when:
* You want to return an instance of a subclass instead of the class itself, 
* You want to implement a singleton (the Singleton pattern),
* You want to return an instance from a cache.
```java
class Singleton {
    static final Singleton _singleton = Singleton._internal();
    factory Singleton() {
        return _singleton;
    }
    Singleton._internal();
}
```

## 3.3. const keyword
```java
// type of 'number' is int
const number = 5
// explicitly write the type const 
String name = 'Alberto';
```
* **final**: Use it when the value is not known at compile time
* **const**: Use it when the value is computed at compile time
```java
final contents = File('myFile.txt').readAsString();
// const contents = File('myFile.txt').readAsString();
// ^ does not compile!
```

## 3.4. Getters and setters
```java
class Fraction {
    int _numerator;
    int _denominator;
    Fraction(this._numerator, this._denominator);
    // Getters are read-only
    int get numerator => _numerator;
    int get denominator {
        return _denominator;
    }
}
```
## 3.5. Operators overload
```java
class Fraction {
    Fraction operator+(Fraction other) =>
    Fraction(
        _numerator * other._denominator +
        _denominator * other._numerator,
        _denominator * other._denominator
    );
    Fraction operator-(Fraction other) => ...
    Fraction operator*(Fraction other) => ...
    Fraction operator/(Fraction other) => ...
}

// 2/5
final frac1 = Fraction(2, 5); 
// 1/3
final frac2 = Fraction(1, 3);
// 2/5 + 1/3 = 11/15
final sum = frac1 + frac2
```

## 3.6. Cloningobjects
```java
class Person {
  final String name;
  final int age;
  const Person({
    required this.name,
    required this.age,
  });
  Person copyWith({
    String? name,
    int? age,
  }) =>
      Person(name: name ?? this.name, age: age ?? this.age);
}
```

# 4. Inheritance and Exceptions
```java
class A {}
class B extends A {}
```
* In Java for example you can write **final class A {}** to say "hey, you can’t inherit from me" but in Dart there is no equivalent.
* The **abstract** keyword defines a class that cannot be directly instantiated: only its derived classes can
* Dart does not have an **interface** keyword and you have to use classes to create interfaces.

#### extends vs implements
**extends**. 
* used when you want to add some missing features in a subclass.
* you don’t need to override every method, getter or setter

**implements**. 
* you need to override every method, getter or setter
* useful when you don’t want to provide an implementation of the functions but just the API.
#### Mixin
A **mixin** is simply a class with no constructor that can be "attached" to other classes to reuse the code without inheritance.
```java=
mixin Swimming {
  void swim() => print("Swimming");
  bool likesWater() => true;
}

class Human with Walking {
  final String _name;
  final String _surname;
  Human(this._name, this._surname);
  void printName() => "$_name $_surname";
}

void main() {
  final me = Human("Alberto", "Miola");
  // prints "Alberto Miola"; method is defined in the class
  me.printName();
  // prints "Walking"; method is not defined in the class // but it's "copied" and "pasted" from the mixin. me.walk();
}

```
#### Exception
```java
class Fraction {
  int _numerator;
  int _denominator;
  Fraction(this._numerator, this._denominator) {
    if (_denominator == 0) {
      throw IntegerDivisionByZeroException();
    }
  }
}

void main() {
  try {
    final f = Fraction(1, 0);
  } on IntegerDivisionByZeroException {
    print("Division by zero!");
  } on FormatException {
    print("Invalid format!");
  } finally {
    print("Always here");
  }
}
```
# 5. Generics and Collections
### Generics
```java=
class Cache<T> {
  final T _obj;
  T get value => _obj;
  // Constructor, setters, methods...
}

void main() {
  final cache = Cache<int>(20);
  String value = cache.value; // Error!
}
```
### Collections
* List
* Set
* Map

# 6. Asynchronous programming
## 6.1. Introduction
User hate when the application "freezes" for a moment or if it doesn’t always react immediately to inputs
Some situations:
> *  database operations;
> * usage of the internet connection, which might be slow and thus the entire process could take longer than expected;
> * many I/O operations might slow down your app’s performances due to the policies adopted by the OS.

In the worst case, the user has to wait a few seconds. You must use asynchronous programming to show something like an animated progress bar while, at the same time, data are processed in the background

## 6.2. Futures
*A Future<T> represents a value or an error that will be available in the future

```java=
Future<int> processData(int param1, double, param2) {
  var value = 0;
  for (var i = 0; i < param1; ++i) {
    for (var j = 0; j < param1 * param2; j++) {
      // a lot of work here...
    }
  }
  final res = httpGetRequest(value);
  return Future<int>.value(res);
}

void main() {
  Future<int> val = processData(1, 2.5);
  val.then((result) => print(result))
     .catchError((e) => print(e.message));
}
```

### async and await
```java
void main() async {
  final data = await processData(1, 2.5);
  print("result = $data");
}
```
> 1. You can use await only in a function marked with async.
> 2. To define an asynchronous functions, put the async keyword before the body. 
> 3. You’re allowed to call await only on a Future<T>.

## 6.3. Stream
In Dart a **stream** is a sequence of asynchronous or synchronous events we can listen to.
![](https://i.imgur.com/cDg27kz.png)
* **Generator**. Creates new data and sends them over the stream.
* **Stream**. It’s the place in which the generated data flow.
* **Subscribers**. A subscriber is someone interested in the data travelling in the stream.

There are two types of generators:
* **Asynchronous generators**: they return a Stream<T> object.
* **Synchronous generators**: they return an Iterable<T> object

A Flutter developer is used to work with Stream<T> because the framework has many asynchronous generators

```java
Stream<int> randomNumbers() async* { //async* allows use yield to emit data
  final random = Random();
  yield random.nextInt(10);
  yield random.nextInt(20); //keyword pushes data on the stream.
}
```

## 6.4. Isolates
Java and C# have a very wide API to work with multiple threads and parallel computation.
**Dart**: 
* There’s only a single thread with its own memory. You cannot create multiple threads
* The Dart code (and thus Flutter applications) is run inside an **isolate** which has its own private area of memory and an event loop
![](https://i.imgur.com/fWVPYQq.png)

> All the threads living on a process share the same memory. You need to be aware of this because writing the same data, at the same time, in the same memory area.

### Multiple isolates and Flutter
* A single Dart application can have more than a single **isolate**; you can create them by using Isolate.spawn() from the **"dart:isolate"** library.
* Isolates have their own event loop and memory area, there are no dependencies or shared components at all. The only way they have to communicate is via **messages**.
![](https://i.imgur.com/U3m37bY.png)
