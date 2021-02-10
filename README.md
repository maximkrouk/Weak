# Weak

[![SwiftPM 5.3](https://img.shields.io/badge/📦_spm-5.3-ED523F.svg?style=flat)](https://swift.org/download/) [![@maximkrouk](https://img.shields.io/badge/contact-@maximkrouk-1DA1F2.svg?style=flat&logo=twitter)](https://twitter.com/maximkrouk)

A mechanism for safe capturing & weakifying objects in Swift.

## Usage Examples

```swift
Without Weak
```

```swift
With Weak
```

----

Default
```swift
{ [weak self] in 
    guard let self = self else { return }
    /// ...
}
```

```swift
capture { _self in
    /// ...
}
```

----

Multiple parameters
```swift
{ [weak self] a, b, c in 
    guard let self = self else { return }
    /// ...
}
```

```swift
capture { _self, a, b, c in 
    /// ...
}
```

---

Methods

```swift
{ [weak self] in 
    guard let self = self else { return }
    self.someMethod()
}
```

```swift
capture(in: Self.someMethod)
```

----

Return values

```swift
let object.dataSource = { [weak self] in
    guard let self = self else { return [] }
    return self.data
}
```

```swift
let object.dataSource = capture(or: [], in: \.data)
```

## Installation

### Basic

You can add DeclarativeConfiguration to an Xcode project by adding it as a package dependency.

1. From the **File** menu, select **Swift Packages › Add Package Dependency…**
2. Enter [`"https://github.com/maximkrouk/weak"`](https://github.com/maximkrouk/weak) into the package repository URL text field
3. Choose products you need to link them to your project.

### Recommended

If you use SwiftPM for your project, you can add DeclarativeConfiguration to your package file. Also my advice is to use SSH.

```swift
.package(url: "git@github.com:maximkrouk/weak.git", .branch("main"))
```

or

```swift
.package(url: "git@github.com:makeupstudio/swift-declarative-configuration.git", .exact("1.0.0"))
```

Do not forget about target dependencies:

```swift
.product(
    name: "Weak", 
    package: "Weak"
)
```

## License

This library is released under the MIT license. See [LICENSE](./LICENSE) for details.

