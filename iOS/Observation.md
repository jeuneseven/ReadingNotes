# What is observation?

- Tracks changes to properties
- @Observable is a macro 
	- When body is executed, SwiftUI tracks access to properties of @Observable types
	- If property isn’t accessed, SwiftUI won’t track it and won’t invalidate the view if the property changes
	- Computed properties will be tracked if they refer to a stored property

# Property Wrappers



# Takeaways

- @Observable is a macro for automating property observation.
- Can be overridden manually in specific cases if required.
- New projects should use @Observable.
- Simplifies models and views.
- Performance boost.

# References

[WWDC](https://developer.apple.com/videos/play/wwdc2023/10149/)

[WWDC Notes](https://wwdcnotes.com/documentation/wwdc23-10149-discover-observation-in-swiftui/)

[Documentation](https://developer.apple.com/documentation/observation)