[Swift Concurrency by Example](https://www.hackingwithswift.com/quick-start/concurrency)

# Introduction
## Concurrency vs parallelism

> Concurrency is about dealing with many things at once, parallelism is about doing many things at once. Concurrency is a way to structure things so you can maybe use parallelism to do a better job.

> -- Rob Pike

## Understanding threads and queues



## Main thread and main queue: what’s the difference?

- main queue will always execute on the main thread (and is therefore where you’ll be doing your UI work!)
- other queues might sometimes run on the main thread – the system is free to move things around in whatever way is most efficient
- if you’re on the main queue then you’re definitely on the main thread
- but being on the main thread doesn’t automatically mean you’re on the main queue – a different queue could temporarily be running on the main thread

## Where is Swift concurrency supported?

- Swift concurrency is supported from iOS 13, macOS 10.15, watchOS 6, tvOS 13, and visionOS 1.0.

# Async/await



# Sequences and streams



# Tasks and task groups



# Actors 



# Testing



# Solutions