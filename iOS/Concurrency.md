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
	- This order restriction is arbitrary, but it's not harmful, and it eliminates the potential for stylistic debates.

## What calls the first async function?



## What’s the performance cost of calling an async function?



## How to create and use async properties?



## How to call an async function using async let?



## Sending data safely across actor boundaries



## What’s the difference between await and async let?



## Why can’t we call async functions using async var?



## How to use continuations to convert completion handlers into async functions?



## How to create continuations that can throw errors?



## How to store continuations to be resumed later?



## How to fix the error “async call in a function that does not support concurrency”



# Sequences and streams



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