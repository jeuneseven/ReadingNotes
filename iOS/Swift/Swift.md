[Swift for Complete Beginners](https://www.hackingwithswift.com/quick-start/beginners)

# Introduction
## Why Swift?

- no cruft
- no confusion

## About this course

- spends more time on the subset of features that matter the most – the ones you’ll use in every app you build, time and time again
- each chapter of this book is available as both text and video, but they cover exactly the same material so you’re welcome to learn whichever way suits you best
- Programming is an art: don't spend all your time sharpening your pencil when you should be drawing.

## How to follow along

- type the code into your computer, run it and see the output, then experiment a little to make sure you understand it

# Simple data
## How to create variables and constants

```
var greeting = "Hello, playground"

```

- var : create a new variable
- greeting : variable name
- = : assigns a value to our variable. You don’t need to have those spaces on either side of the equals sign if you don’t want to, but it’s the most common style
- “Hello, playground” : the value we’re assigning, written inside double quotes, so that Swift can see where the text starts and where it ends
- doesn’t need a semicolon at the end of the line. Swift does allow semicolons, but they are very rare, you’ll only ever need them if you want to write two pieces of code on the same line for some reason
- When you make a variable, you can change it over time, you can change variables as much as you need to, and the old value is discarded each time

```
let character = "Daphne"

```
- use let we make a constant, which is a value that can’t change. Swift literally won’t let us, and will show a big error if we try
- let: comes from the mathematics world, where they say things like “let x be equal to 5.”
- camel case: the second and subsequent words in a name start with a little bump for the capital letter
- prefer to use constants rather than variables – not only does it give Swift the chance to optimize your code a little better, but it also allows Swift to make sure you never change a constant’s value by accident

## How to create strings

- start and end with double quotes
- use other double quotes inside your string, as long as you’re careful to put a backslash before them so that Swift understands they are inside the string rather than ending the string

```
let quote = "Then he tapped a sign saying \"Believe\" and walked away."
```

- use three quotes show multi-line strings: the triple quotes at the start and end are on their own line, with your string in between

```
let movie = """
A day in
the life of an
Apple engineer
"""
```

- you can read the length of a string by writing .count after the name of the variable or constant

```
print(actor.count)
```

- uppercased(): sends back the same string except every one of its letter is uppercased
	- if you’re asking Swift to read some data you don’t need the parentheses, but if you’re asking Swift to do some work you do

```
print(result.uppercased())
```

- hasPrefix()/hasSuffix(): lets us know whether a string starts with some letters of our choosing; checks whether a string ends with some text

```
print(movie.hasPrefix("A day"))

print(filename.hasSuffix(".jpg"))
```

- Strings are case-sensitive in Swift, which means using filename.hasSuffix(".JPG") will return false because the letters in the string are lowercase

## How to store whole numbers

- integers、Int: originally a Latin word meaning “whole”
- you can use underscores, _, to break up numbers however you want

```
let reallyBig = 1_00__00___00____00
```
- compound assignment operators: *=、-=、/=、+=

## How to store decimal numbers

- Double: double-precision floating-point number, Swift allocates twice the amount of storage as some older languages would do, meaning a Double can store absolutely massive numbers.
- Swift considers decimals is different type of data to integers, you can’t mix them together(called type safety). Integers are always 100% accurate, decimals are not, so Swift won’t let you put the two of them together unless you specifically ask for it to happen: 

```
let a = 1
let b = 2.0
let c = a + b // error

let c = a + Int(b) ✅
let c = Double(a) + b ✅
```
- Swift decides whether you wanted to create a Double or an Int based on the number you provide, if there’s a dot in there, you have a Double, otherwise it’s an Int. Even if the numbers after the dot are 0.
- decimal numbers have the same range of operators and compound assignment operators as integers
- Swift lets us use regular Double numbers everywhere a CGFloat is expected, so although you will see CGFloat appear from time to time you can just ignore it.
- the reason floating-point numbers are complex is because computers are trying to use binary to store complicated numbers.

## How to store truth with Booleans

- Booleans don’t have arithmetic operators
- Booleans have one special operator, !, which means “not”, this flips a Boolean’s value from true to false, or false to true
- Booleans do have a little extra functionality that can be useful. In particular, if you call toggle() on a Boolean it will flip a true value to false, and a false value to true

## How to join strings together



## Summary: Simple data



## Checkpoint 1



# Complex data
## How to store ordered data in arrays



## How to store and find data in dictionaries



## How to use sets for fast data lookup



## How to create and use enums



## How to use type annotations



## Summary: Complex data



## Checkpoint 2



# Conditions and loops
## How to check a condition is true or false



## How to check multiple conditions



## How to use switch statements to check multiple conditions



## How to use the ternary conditional operator for quick tests



## How to use a for loop to repeat work



## How to use a while loop to repeat work



## How to skip loop items with break and continue



## Summary: Conditions and loops



## Checkpoint 3


# Functions
## How to reuse code with functions



## How to return values from functions



## How to return multiple values from functions



## How to customize parameter labels



## How to provide default values for parameters



## How to handle errors in functions



## Summary: Functions



## Checkpoint 4


# Closures
## How to create and use closures



## How to use trailing closures and shorthand syntax



## How to accept functions as parameters



## Summary: Closures



## Checkpoint 5



# Structs
## How to create your own structs



## How to compute property values dynamically



## How to take action when a property changes



## How to create custom initializers



## How to limit access to internal data using access control



## Static properties and methods



## Summary: Structs



## Checkpoint 6


# Classes
## How to create your own classes



## How to make one class inherit from another



## How to add initializers for classes



## How to copy classes



## How to create a deinitializer for a class



## How to work with variables inside classes



## Summary: Classes



## Checkpoint 7


# Protocols and extensions
## How to create and use protocols



## How to use opaque return types



## How to create and use extensions



## How to create and use protocol extensions



## How to get the most from protocol extensions



## Summary: Protocols and extensions



## Checkpoint 8



# Optionals
## How to handle missing data with optionals



## How to unwrap optionals with guard



## How to unwrap optionals with nil coalescing



## How to handle multiple optionals using optional chaining



## How to handle function failure with optionals



## Summary: Optionals



## Checkpoint 9



# Wrap up
## Where now?

[100 Days of SwiftUI](https://www.hackingwithswift.com/100/swiftui)