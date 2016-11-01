---
layout: default
---

# Welcome To Swift

Hey, thanks for checking out the microsite for my "Welcome to Swift" talk!
I built this site to compliment my talk for [Activate](http://activateconf.com/) in Baton Rouge on November 3rd, 2016.

This talk provides a "swift" introduction to Apple's new programming language for iOS, watchOS, MacOS, and tvOS.
We'll review some of Swift's primary language features before diving into Xcode to demo the language by building a bare bones iOS app.
You'll walk away with some basic knowledge about the Swift ecosystem and insight into where to look to learn more.

## What is Swift?

Swift can be described many ways.
Formally it is a "compiled, statically typed, object oriented language".
More casually, it is a language developed by Apple for people building for their platforms, e.g. iOS, macOS, tvOS and watchOS.


Apple introduced us to Swift in June 2014.
At that time they described it as "Objective-C" without the C.
So what is Objective-C?
Objective-C is an object oriented variant of C, and prior to 2014 it was the primary programming language for iOS and OS X.


So, when Apple said that Swift was "Objective-C without the C", they were saying it has all the power of Objective-C but with a more modern syntax and updated language features.
At the time, this was evidenced by the tight relationship between the two languages.
All of the old libs Apple had written for Objective-C were available to us in Swift, and, we could compile our old Objective-C code and our Swift code right alongside each other in the same app.


In December of 2015, Apple open sourced Swift.
The code used to build the Swift compiler and its peripherals are available to the public.
Apple also published [Swift.org](https://swift.org) which serves as a roadmap for Swift's development and resources for developers and contributors.

## Where do I get Swift

### Mac Users

If you are a Mac user, Swift is comes built in.
You can open a terminal and type `swift` and hit enter to start a Swift REPL.
Here you can type Swift code and see the results of its execution.

To take full advantage of the language you'll want to install [Xcode](https://developer.apple.com/xcode/).
Xcode is an IDE for Swift which contains all the tools you'll need to build applications.
Xcode also offers [interactive playgrounds](https://developer.apple.com/swift/blog/?id=35) which is a handly tool for prototyping and playing around with the Swift programming language.

### iOS Users

iPad users can download the [Swift Playgrounds](http://www.apple.com/swift/playgrounds/) iOS app.
This app includes some interactive puzzles that are solved by writing Swift code.

### Linux Users

Linux users can also use the Swift programming language.
[Swift.org](https://swift.org/getting-started/#installing-swift) has some information about installing Swift on a system running Linux.

### Windows Users

¯\\\_(ツ)\_/¯

## Language Features

Let's review some of Swift's syntax and language features.

This review of language is by no means comprehensive.
Check out [Apple's documentation](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html) for a more thorough overview of the language.

### Constants & Variables

In Swift, variables are declared with the `var` keywoard.
A variable's value can be changed to a different value of the same type after it has been set.

```swift
var a = 5
```

Like a variable, a constant associates a name with a value.
Unlike a variable, a constant's value cannont be changed after it has been set.

Constants are declared with the `let` keyword:

```swift
let b = 6
```

Type annotations can be used to describe a constant or variable's type explicitly.
If no type annotation is provided, the constant or variable's type is infered from the value assigned.


```swift
let a: Int = 4
let c: String = "hello!"
```

### Optionals

Swift has a concept of "optional types".
This is similar to `nil` or `null` in other programming languages.

When a variable has an optional type that means that the variable can either have a value, or the absence of a value.
In Swift the absence of a value is described as `nil`.

Optional types are described using a `?`.

```swift
var optionalString: String? = "this could be nil. who knows? maybe?"
optionalString = nil  // no worries here

var nonoptionalString: String = "this cannot be nil"
nonoptionalString = nil  // this will explode
```

Before you can use the value in an optional, you must "unwrap" it.
Optionals can be unwrapped with the `!`.

If you attempt to unwrap an optional that is nil, your program will crash and die.

```swift
var optionalInt: Int? = 5
optionalInt! + 5  // no worries. returns 10

optionalInt = nil
optionalInt! + 5  // this will explode.
```

Optionals can be "implicitly unwrapped" if you defined them with a `!` instead of a `?`.
Implicitly unwrapped optionals do not need a `!` to unwrap them.

Be careful because attempting to access an implicitly unwrapped optional that is nil will crash your program.

```swift
var unwrappedOptionalInt: Int! = 5
unwrappedOptionalInt + 5  // no worries. returns 10

unwrappedOptionalInt = nil
unwrappedOptionalInt + 5  // this will explode.
```

### Comments

Swift uses the `//` syntax for single line comments and the `/* */` sytax for mutliline comments.

```swift
// This is a single line comment
/* This is a multiline comment.
   It spans many lines */
```

You can use `/** */` or `///` for documentation comments.

If you document something in this way Xcode can help you refence that documentation later.
For example, if you document a function, you can option + click the name of that function where it appears later in your code and see the documentation in a tooltip.

```swift
/**
 This function doubles an integer
*/
func double(value: Int) -> Int {
    return value * 2
}

/// This function halves an integer
func halve(value: Int) -> Int {
    return value / 2
}
```

Here's an example of what this looks like in Xcode:

![Xcode documentation tooltip](/assets/screenshots/language-features/comments-documentation-tooltip.png)

### Numbers

The most common numberic types in Swift are `Int` and `Double`.
Additionally, you may see `UInt` which is an unsigned integer, `Int64` and `Int32` which are 64-bit and 32-bit integers respectively, and `Float` which is a floating point number.

```swift
let integer: Int = 5
let double: Double = 5.0

let unsignedInteger: UInt = 3

let int64Bit: Int64 = 6
let int32Bit: Int32 = 7

let float: Float = 2.7
```

### Strings

Swift has a string type named `String`.
Strings are declared using double quotes: `"`.


```swift
let helloWorld = "Hello, world!"
```

Strings are described as a collection of characters which conform to the `Character` type.
A character can be defined using a type annotation with a single character string.

```swift
let characterH: Character = "H"
```

### Operators

Swift uses `=` for the assignment operator.
Swift also has compound assignment operators.

```swift
var a = 5  // a now equals 5
```

Swift has all of the basic arithmetic operators you would expect in a programming language:

```swift
1 + 2      // equals 3
3 - 4      // equals -1
5 * 6      // equals 30
7.0 / 8.0  // equals 0.875
```

These operators can be used on more than numeric values:

```swift
"hello, " + "world"  // equals "hello, world"
```

Swift also has all the basic comparison operators you'd expect in a programming language:

```swift
1 == 0   // false
2 != 1   // true
3 > 2    // true
4 < 3    // false
5 >= 4   // true
6 <= 5   // false
```

...and a standard set of built-in logical operators.

```swift
!true          // false
true || false  // true
true && false  // false
```

There's plenty of other fun operators that I don't have time to go into here, but here's a quick preview of some:

```swift
// The nil-coalescing operator
a ?? b
// The closed-range operator
1...5
// The half-open range operator
1..<5
// The ternary conditional operator
question ? "It's true!" : "It's false!"
// The remainder operator (different from a formal modulus operator, look it up!)
6 % 4
// The bitwise AND operator
0b11111100 & 0b00111111
```

To make things more exciting, Swift gives you the ability to overload operators and change their behavior.
Additionally, you can define custom operators.
Unfortunatly, I will not have the time to go too in depth with that here.

```swift
infix operator <!!>

extension Int {
  static func <!!>(a: Int, b: Int) -> Int {
    return (a + b) * 42
  }
}

4 <!!> 5  // equal 378, or (4 + 5) * 42
```

### Collections

Swift's most common collection types are `Array` and `Dictionary`.
Arrays represent ordered collections of objects and dictionaries represent key-value pairs.

#### Arrays

An array's type is described according to the type of elements it contains.
For example, an array of integers would use the type `[Int]`.

```swift
var arrayOfInts = [1, 2, 3]
var explicitArrayOfInts: [Int] = [4, 5, 6]
var emptyArrayOfInts = [Int]()
```

Arrays values can be accessed using indexes as subscripts.

```swift
arrayOfInts[1] // returns 2
```

Additionally, there's a rich set of methods that can be used to work with Arrays.
Here's a few examples:

```swift
arrayOfInts.index(of: 3)   // returns 2
arrayOfInts.max()          // returns 3
arrayOfInts.min()          // returns 1
arrayOfInts.append(4)      // now equals [1, 2, 3, 4]
arrayOfInts.count          // returns 4
arrayOfInts.remove(at: 2)  // now equals [1, 2, 4]
arrayOfInts.first          // returns 1
arrayOfInts.last           // returns 4
```

#### Dictionaries

Dictionaries are also described according the the types of elements they contain.
For example, a dictionary with keys of the type `String` and values of the type `Int` would use the type `[String: Int]`

```swift
var numbers = [
  "one": 1,
  "two": 2,
  "three": 3,
]
var emptyDictionary = [String: Float]()
var explicitDictionary: [Character: String] = [
  "a": "ay",
  "b": "bee",
  "c": "see"
]
```

Dictionary values can be accessed using the keys as subscripts.

```swift
numbers["one"] // returns 1
```

Like arrays, dictionaries provide a wide range of methods to those wishing to work with them.
Here's a quick overview of a limitted set of those methods:

```swift
numbers.count                            // 3
numbers.isEmpty                          // false
numbers.removeValue(forKey: "two")       // key/value for "two" removed
numbers.updateValue(4, forKey: "three")  // numbers["three"] now equals 4
numbers.removeAll()                      // numbers is now empty
```

### Control Flow

Swift has a wide array of built in statements to handle control flow.
I'm only able to cover a few here.
For a more comprehensive overview check out [Apple's documentation](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/ControlFlow.html).

#### If/Else

If statements work the same way they do in other programming language.
Parentheses are optional.

```swift
var number = 5

if number == 5 {
  // do something
}

if number > 5 {
  // do something
} else {
  // do something else
}

if number > 5 {
  // do something
} else if number == 5 {
  // do something else
} else {
  // do something... elser...?
}
```

If statements can also be used with `let` to unwrap optionals.

This example if effectively saying: "If `optionalNumber` is not nil, assign it to the variable `optionalNumber` within the if statement's scope and print it out.
If `optionalNumber` is nil, print out `"optionalNumber is nil"`."

```swift
var optionalNumber: Int? = 5

if let optionalNumber = optionalNumber {
  // optionalNumber is now available as an unwrapped optional
   print(optionalNumber)
} else {
  // optionalNumber is nil
  print("optionalNumber is nil")
}
```

#### Guard

Guard statements work similarly to if statements.
They provide an else block which is executed if the conditional is false.

This is helpful for early exit from a function.

```swift
func fibonacci(at number: Int) -> Int {
  guard number > 1 else {
    return number
  }

  return fibonacci(at: number - 1) + fibonacci(at: number - 2)
}

fibonacci(at: 7)  // return 13
```

#### While Loops

#### For Loops

#### Switch Statements

### Functions

TODO

### Classes

TODO

## Demo

TODO
