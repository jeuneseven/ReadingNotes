[SwiftData by Example](https://www.hackingwithswift.com/quick-start/swiftdata)

# Introduction
## What is SwiftData?

- SwiftData supports only iOS 17 or later, macOS Sonoma, tvOS 17, watchOS 10, and visionOS 1.0
- great choice for on-device storage, including:
	- Permanent storage of user data
	- Temporary storage of user data, where SwiftData is used as a cache for data fetched from a server
	- Document-based apps, e.g. text or video editors
	- Complex user settings or history data
- less of a great choice when:
	- You need to support many users using iOS 16 and earlier
	- Your data is stored only in CloudKit or another equivalent service, and you need to be using live data at all times
	- You need the full range of capabilities offered by Core Data

## SwiftData vs Core Data

- SwiftData builds on top of Core Data, a few major Core Data features are not yet supported for developers working exclusively in SwiftData, including:

1. We don’t have an equivalent of NSCompoundPredicate, for creating complex, multi-step predicates.
2. We don’t have an equivalent of NSFetchedResultsController, for executing then monitoring queries for changes.
3. There is no support for derived attributes, so things like an automatic lastUpdated property aren’t possible.
4. There are no sectioned fetched requests.
5. SwiftData does not support abstract classes or child contexts.
6. Or pinning to a specific query generation.

## Should you learn SwiftData, Core Data, or both?

- if you are able to live without the missing features such as NSFetchedResultsController, and you are able to target iOS 17 and later, learning SwiftData is significantly faster and easier – you’ll be building apps in a tenth the time it would take for you to learn Core Data

## Frequently asked questions about SwiftData



## How to follow this quick start guide



## Migrating from Core Data to SwiftData



## Dedication



# Building a complete project



# Containers and context



# Defining your data model



# Creating relationships



# Working with data



# Handling migration



# Building with SwiftData



# Architecture



# Solving problems
