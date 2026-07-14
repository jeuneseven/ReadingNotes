[Swift Concurrency by Example](https://www.hackingwithswift.com/quick-start/concurrency)

# Introduction
## Concurrency vs parallelism

> Concurrency is about dealing with many things at once, parallelism is about doing many things at once. Concurrency is a way to structure things so you can maybe use parallelism to do a better job.

> -- Rob Pike

## Understanding threads and queues

- main thread: always exists for the lifetime of the app, all user interface work must take place on main thread, if try to update UI from any other thread in program might find nothing happens, might find app crashes, or pretty much anywhere in between, this rule exists for all apps that run on iOS, macOS, tvOS, and watchOS
- context switch: swapping threads
	- it has a performance cost: the system must stash away all the data the thread was using and remember how far it had progressed in its work, before giving another thread the chance to run
	- thread explosion: when create many more threads compared to the number of available CPU cores, the cost of context switching grows high
- queues: we create a queue and add work to it, and the system will remove and execute work from there in the order it was added
	- serial: remove one piece of work from the front of the queue and complete it before going onto the next piece of work
	- concurrent: remove and execute multiple pieces of work at a time
	- Either way work will start in the order it was added to the queue unless we specifically say something has a high or low priority
- threads are the individual slices of a program that do pieces of work, whereas queues are like pipelines of execution where we can request that work be done at some point

## Main thread and main queue: what’s the difference?

- main queue will always execute on the main thread (and is therefore where you’ll be doing your UI work!)
- other queues might sometimes run on the main thread – the system is free to move things around in whatever way is most efficient
- if you’re on the main queue then you’re definitely on the main thread
- but being on the main thread doesn’t automatically mean you’re on the main queue – a different queue could temporarily be running on the main thread

## Where is Swift concurrency supported?

- Swift concurrency is supported from iOS 13, macOS 10.15, watchOS 6, tvOS 13, and visionOS 1.0.

# Async/await
## What is a synchronous function?

- By default, all Swift functions are synchronous
	- A synchronous function is one that executes all its work in a simple, straight line on a single thread
- stack frame: whenever one function calls another, the system create to store all the data(e.g. local variables) required for that new function
- new stack frame gets pushed on top of the previous one, eventually the functions finish, and their stack frame is removed and destroyed in a process we call popping, and control goes back to whichever function the code was called from
- downside: blocking

## What is an asynchronous function?

- async is part of the function’s type
- await: run this function asynchronously and wait for its result to come back before continuing

1. when an async function is suspended, all the async functions that called it are also suspended; they all wait quietly while the async work happens, then resume later on; for this reason that synchronous functions cannot call async functions directly – they don’t know how to suspend themselves
2. a function can be suspended as many times as is needed, but it won’t happen without you writing await there – functions won’t suspend themselves by surprise
3. a function that is suspended does not block the thread it’s running on, and instead it gives up that thread so that Swift can do other work instead
4. when the function resumes, it might be running on the same thread as before, but it might not; Swift gets to choose, and you shouldn’t make any assumptions here
5. just because a function is async doesn’t mean it will suspend – the await keyword only marks a potential suspension point

## How to create and call an async function?

1. declaring the function itself as being async
2. calling that function using await

- Swift will run each of the await calls in sequence, waiting for the previous one to complete. This is not going to run several things in parallel

## How to call async throwing functions?

- mark the function as being async throws, call the function using try await – the keyword order is flipped, think of it as unwinding a stack
	- This order restriction is arbitrary, but it's not harmful, and it eliminates the potential for stylistic debates

## What calls the first async function?

if only async functions can call other async functions, what starts it all – what calls the very first async function?

1. in simple command-line programs using the @main attribute, you can declare your main() method to be async. This means your program will immediately launch into an async function, so you can call other async functions freely
2. in SwiftUI, the framework itself has various places that can trigger an async function. For example, the refreshable() and task() modifiers can both call async functions freely
	- When do async work you might end up pushing work away from the main thread where UI updates must happen, but the @State property wrapper has specifically been written to allow us to modify its value on any thread
3. Swift provides a dedicated Task API that lets us call async functions from a synchronous function

## What’s the performance cost of calling an async function?

- synchronous and asynchronous functions use a different calling convention internally, with the asynchronous variant being slightly less efficient
	- Swift cannot tell at compile time whether an await call will suspend or not, and so the same (slightly) more expensive calling convention is used regardless of what actually takes place at runtime
- What happens at runtime depends on whether the call suspends or not:
	- If a suspension happens, then Swift will pause the function and all its callers, which has a small performance cost. These will then be resumed later, and ultimately whatever performance cost you pay for the suspension is like a rounding error compared to the performance gain provided by async/await even existing
	- If a suspension does not happen, no pause will take place and your function will continue to run with the same efficiency and timings as a synchronous function
	- using await will not cause your code to wait for one runloop to go by before continuing
- if your code doesn’t actually suspend, the only cost to calling an asynchronous function is the slightly more expensive calling convention, and if your code does suspend then any cost is more or less irrelevant because you’ve gained so much extra performance thanks to the suspension happening in the first place

## How to create and use async properties?

- computed properties can be asynchronous: attempting to access them must also use await or similar, and may also need throws if errors can be thrown when computing the property

## How to call an async function using async let?

- async let: run several async operations at the same time then wait for their results to come back
	- it captures any values it uses, which means you might accidentally try to write code that isn’t safe
	- don’t need to use await before async func because that’s implied by async let
	- don’t need to use try to execute async func because that gets pushed back to when we actually want to read its return value
- The Swift compiler will automatically track which async let constants could throw errors and will enforce the use of try when reading their value. It doesn’t matter which form of try you use, so you can use try, try? or try! as appropriate
- If you never try to read the value of a throwing async let call – i.e., if you’ve started the work but don’t care what it returns – then you don’t need to use try at all, which in turn means the function running the async let code might not need to handle errors at all
- if you wanted to update your user interface as soon as data arrived back, async let isn’t going to help by itself you should look at the dedicated Task type instead

## Sending data safely across actor boundaries

- Swift tries to ensure access to shared data is done safely, partly through types such as actors, and partly through a concept of sendability implemented through the Sendable protocol and the @Sendable attribute

## What’s the difference between await and async let?



## Why can’t we call async functions using async var?



## How to use continuations to convert completion handlers into async functions?



## How to create continuations that can throw errors?



## How to store continuations to be resumed later?



## How to fix the error “async call in a function that does not support concurrency”



# Sequences and streams



## What’s the difference between Sequence, AsyncSequence, and AsyncStream?



## How to loop over an AsyncSequence using for await?



## How to manipulate an AsyncSequence using map(), filter(), and more?



## How to create a custom AsyncSequence?



## How to convert an AsyncSequence into a Sequence?



## How to create and use AsyncStreams to return buffered data?



# Tasks and task groups



# Actors 



# Testing
## Introduction to testing Swift concurrency



## How to write basic async tests



## How to handle concurrency errors in unit tests



## How to test completion handlers with Swift Testing and XCTest



## How to test AsyncSequence and AsyncStream



## How to set a time limit for concurrent tests



## How to force concurrent tests to run on a specific actor



## How to serialize parameterized tests with Swift Testing



# Solutions