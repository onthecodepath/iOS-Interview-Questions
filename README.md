# iOS-Interview-Questions

A collection of iOS interview questions and answers in one place.

- [Core Data](https://github.com/onthecodepath/iOS-Interview-Questions#core-data)
    - What is Core Data?
    - What is an object managed model?
    - What is an object managed coordinator?
    - What is an object managed context?
- [General/Uncategorized](https://github.com/onthecodepath/iOS-Interview-Questions#general--uncategorized)
    - What is the difference between a stack vs a heap?
    - What is the difference between a class and an object?
    - What is the delegation pattern?
    - What is MVC and MVVC?
    - What is JSON?
    - What is the difference between _name vs self.name?
- [Memory Management](https://github.com/onthecodepath/iOS-Interview-Questions#memory-management)
    - What is the difference between copy and retain?
- [Thread Management](https://github.com/onthecodepath/iOS-Interview-Questions#thread-management)
    - What is the difference between atomic and non-atomic synthesized properties?


## Core Data
What is Core Data?

What is an object managed model?

What is an object managed coordinator?

What is an object managed context?

## General / Uncategorized
What is the difference between a stack vs a heap?

What is the difference between a class and an object?

What is the delegation pattern?

What is MVC and MVVC?

What is JSON?

What is the difference between _name vs self.name?

## Memory Management

**What is the difference between *copy* and *retain*?**

Calling *retain* on an object will increase its *retain* count by one. When the *retain* count of an objective reaches 0, the object will be deallocated and released from memory.

When you *retain* an object, you share the same version with whoever passed the object to you. But when you *copy* an object, you do not share the same version of the object that was passed to you. Instead, a duplicate of that object is created with duplicated values.

## Thread Management

**What is the difference between *atomic* and *non-atomic* synthesized properties?**

First, properties are set to *atomic* by default. 

*Atomic* properties are more likely to guarentee thread-safety because it will ensure that a value is fully set (by the setter method) or fully retrieved (by the getter method) when accessor methods are called simultaneously.

*Non-atomic* properties, howeer are not thread-safe. While they run faster, they may cause race conditions. In the event that accessor methods are called simultaneously and a race condition occurs, a setter value would first release the old value and a getter method would retrieve nil since no value has not been set yet.

## Unit Testing

What is the purpose of unit testing? What are the benefits?


