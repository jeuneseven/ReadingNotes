[Understanding Swift](https://www.hackingwithswift.com/quick-start/understanding-swift)

# Introduction
## The Zen of Swift

- explain why all the key language features are important and useful, so you can understand them in a practical context
- explain why a particular feature is useful in practical software development

## What’s the difference between Swift and SwiftUI?

- Swift: programming language, it’s the words we type into our computer to say what our program should do, can be used in many places, but it’s mostly used for building apps on Apple’s platforms
- SwiftUI: a set of tools that let us describe and control user interfaces 
- Building an app is the process of writing Swift code to control SwiftUI

# Simple types
## Why does Swift have variables?

- allow us to store temporary information in our program, form a key part of almost every Swift program
- Once you create a variable using var, you can change it as often as you want without using var again

## Why is Swift a type-safe language?

- When you create a variable Swift can figure out what type the variable is based on what kind of data you assign to it, and from then on that variable will always have that one specific type
- as programs grow in size and complexity, it becomes impossible to keep the types of your variables in your head at all times, so we’re effectively shifting that work on to Swift instead

## Why does Swift need multi-line strings?

- if you use triple quotes you can write your strings across as many lines as you need, which means the text remains easy to read in your code

## Why does Swift need both Doubles and Integers?

- When creating a numeric variable, Swift decides whether to consider it an integer or a double based on whether you include a decimal point
- Swift is playing it safe: we can both see that 1 plus 1.0 will be 2, but double is a variable so it could be modified to be 1.1 or 3.5 or something else. How can Swift be sure it’s safe to add an integer to a double, how can it be sure you won’t lose the 0.1 or 0.5?

## Why does Swift have string interpolation?

- Swift gives us string interpolation as a way of injecting custom data into strings at runtime: it replaces one or more parts of a string with data provided by us
- Swift is capable of placing any kind of data inside string interpolation

[Super-powered string interpolation in Swift 5.0](https://www.hackingwithswift.com/articles/178/super-powered-string-interpolation-in-swift-5-0)

## Why does Swift have constants as well as variables?

- Swift recommend use constants if you created a variable then never changed its value
- The reason for this is about avoiding problems: any variable you create can be changed by you whenever you want and as often as you want, so you lose some control
- Constants don’t let us change values once they are set, so it’s a bit like a contract with Swift: you’re saying “this value matters, don’t let me change it no matter what I do.”

## Why does Swift have type annotations?

- Swift can’t figure out what type should be used
- You want Swift to use a different type from its default
- You don’t want to assign a value just yet

# Complex types
## Why does Swift have arrays?



## Why are sets different from arrays in Swift?



## How are tuples different from arrays in Swift?



## When should you use an array, a set, or a tuple in Swift?



## Why does Swift have dictionaries as well as arrays?



## Why does Swift have default values for dictionaries?



## Why would you want to create an empty collection?



## Why does Swift need enums?



## Why would you want to associate a value with an enum case?



## Why do Swift’s enums have raw values?



# Operators and conditions
## Why can’t Swift add a Double to an Int?



## Why does Swift have a dedicated division remainder operator?



## Why does Swift need operator overloading?



## Why does Swift have compound assignment operators?



## How does Swift let us compare many types of data?



## What’s the difference between if and else if?



## How to check multiple conditions



## When should you use the ternary operator in Swift?



## When should you use switch statements rather than if?



## Why does Swift have two range operators?



# Looping
## Why does Swift use underscores with loops?



## When should you use a while loop?



## When should you use a repeat loop?



## Why would you want to exit a loop?



## Why does Swift have labeled statements?



## When to use break and when to use continue



## Why would you want to make an infinite loop?



# Functions
## What code should be put in a function?



## How many parameters should a function accept?



## When is the return keyword not needed in a Swift function?



## How can you return two or more values from a function?



## Why does Swift use parameter labels?



## When should you omit a parameter label?



## When to use default parameters for functions



## When to use variadic functions



## When should you write throwing functions?



## Why does Swift make us use try before every throwing function?



## When should you use inout parameters?



# Closures
## What the heck are closures and why does Swift love them so much?



## Why are Swift’s closure parameters inside the braces?



## How do you return a value from a closure that takes no parameters?



## Why would you want to use closures as parameters?



## Why does Swift have trailing closure syntax?



## When would closures with parameters be used as parameters?



## When would you use closures with return values as parameters to a function?



## When should you use shorthand parameter names?



## How many parameters can a closure take?



## Returning closures from functions



## Why do Swift’s closures capture values?



# Structs
## What’s the difference between a struct and a tuple?



## When should you use a computed property or a stored property?



## When should you use property observers?



## When should you use willSet rather than didSet?



## What’s the difference between a function and a method?



## Why do we need to mark some methods as mutating?



## Why are strings structs in Swift?



## Why do strings behave differently from arrays in Swift?



## How do Swift’s memberwise initializers work?



## When would you use self in a method?



## When should properties be lazy?



## What’s the point of static properties and methods in Swift?



## What’s the point of access control?



