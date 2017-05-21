# iOS-Interview-Questions

A collection of iOS interview questions and answers. These concepts are important especially for beginner developer to learn and understand.

- [Core Data](https://github.com/onthecodepath/iOS-Interview-Questions#core-data)
    - What is Core Data?
    - When would you use Core Data over NSUserDefault?
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
**What is Core Data?**

In Apple's [words](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CoreData/index.html?utm_source=iosstash.io), "Core Data is a framework that you use to manage the model layer objects in your application. It provides generalized and automated solutions to common tasks associated with object life cycle and object graph management, including persistence."

**When would you use Core Data over NSUserDefault?**

NSUserDefault is typically used to store small bits of data (settings, preferences, etc.). Core Data is used to store a large list of elements. 

**What is a managed object context?**

First, managed object context is an instance of NSManagedObjectContext. It is the central object in the Core Data stack. It is used to create and fetch managed objects, and to manage undo and redo operations. Although it is allowed to have multiple managed object contexts, there is typically at most one managed object to represent any given record in a persistent store.

## General / Uncategorized
What is the difference between a stack vs a heap?

**What is the difference between a class and an object?**

In the simplest sense, a class is a blueprint for an object. It describes the properties and behaviors common to any particular type of object. An object, on the other hand, is an instance of a class.

What is the delegation pattern?

What is MVC and MVVC?

**What is JSON?**

**What is the difference between _ vs self. in Objective-C?**

You typically use either when accessing a property in Objective-C. When you use _, you're referencing the actual instance variable directly. You should avoid this. Instead, you should use self. to ensure that any getter/setter actions are honored. 

In the case that you would write your own setter method, using _ would not call that setter method. Using self. on the property, however, would call the setter method you implemented. '

## Object Oriented Programming (OOP)

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


