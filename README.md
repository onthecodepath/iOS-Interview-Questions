# iOS-Interview-Questions

An open-source collection of iOS interview questions and answers. These concepts are important especially for beginner developer to learn and understand.

- [Core Data](https://github.com/onthecodepath/iOS-Interview-Questions#core-data)
    - What is Core Data?
    - When would you use Core Data over NSUserDefault?
    - What is an object managed context?
- [General/Uncategorized](https://github.com/onthecodepath/iOS-Interview-Questions#general--uncategorized)
    - What is the difference between a class and an object?
    - What is the delegation pattern?
    - What is MVC?
    - What is JSON?
    - What is the difference between _name vs self.name?
- [Memory Management](https://github.com/onthecodepath/iOS-Interview-Questions#memory-management)
    - What is the difference between copy and retain?
- [Thread Management](https://github.com/onthecodepath/iOS-Interview-Questions#thread-management)
    - What is the difference between atomic and non-atomic synthesized properties?
    - What is the difference between a stack vs a heap?
- [Unit Testing](https://github.com/onthecodepath/iOS-Interview-Questions#unit-testing)
    -What is the purpose of unit testing? What are the benefits?


## Core Data
**What is Core Data?**

In Apple's [words](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CoreData/index.html?utm_source=iosstash.io), "Core Data is a framework that you use to manage the model layer objects in your application. It provides generalized and automated solutions to common tasks associated with object life cycle and object graph management, including persistence."

**When would you use Core Data over NSUserDefault?**

NSUserDefault is typically used to store small bits of data (settings, preferences, etc.). Core Data is used to store a large list of elements. 

**What is a managed object context?**

First, managed object context is an instance of NSManagedObjectContext. It is the central object in the Core Data stack. It is used to create and fetch managed objects, and to manage undo and redo operations. Although it is allowed to have multiple managed object contexts, there is typically at most one managed object to represent any given record in a persistent store.

## General / Uncategorized

**What is the difference between a class and an object?**

In the simplest sense, a class is a blueprint for an object. It describes the properties and behaviors common to any particular type of object. An object, on the other hand, is an instance of a class.

**What is the delegation pattern?**

The delegation pattern is a powerful pattern used in building iOS applications. The basic idea is that one object will act on another object's behalf or in coordination with another object. The delegating object typically keeps a reference to the other object (delegate) and sends a message to it at the appropriate time.'

**What is MVC?**

MVC stands for **Model-View-Controller**. It is a software architecture pattern for implementing user interfaces. 

MVC consists of three layers: the model, the view, and the controller.
- The model layer is typically where the data resides (persistence, model objects, etc)
- The view layer is typically where all the UI interface lies. Things like displaying buttons and numbers belong in the view layer. The view layer does not know anything about the model layer and vice versa.
- The controller (view controller) is the layer that integrates the view layer and the model layer together. 

**What is JSON?**

JSON stands for JavaScript Object Notation. According to [wiki](https://en.wikipedia.org/wiki/JSON), it is a file format that uses human-readable text to transmite data objects consisting of attribute-value pairs and array data types. 

**What is the difference between _ vs self. in Objective-C?**

You typically use either when accessing a property in Objective-C. When you use _, you're referencing the actual instance variable directly. You should avoid this. Instead, you should use self. to ensure that any getter/setter actions are honored. 

In the case that you would write your own setter method, using _ would not call that setter method. Using self. on the property, however, would call the setter method you implemented. '

## Memory / Memory Management

**What is the difference between *copy* and *retain*?**

Calling *retain* on an object will increase its *retain* count by one. When the *retain* count of an objective reaches 0, the object will be deallocated and released from memory.

When you *retain* an object, you share the same version with whoever passed the object to you. But when you *copy* an object, you do not share the same version of the object that was passed to you. Instead, a duplicate of that object is created with duplicated values.

**What is the difference between a stack vs a heap?**

A stack is a region of memory where data is added or removed in a last-in-first-out (LIFO) order. According to [Ates Goral](http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap), it is the memory set aside as scratch space for a thread of execution. Meanwhile the heap is memory set aside for dynamic allocation. Unlike the stack, you can allocate a block at any time and free it at anytime. 

Note: In Objective-C, all objects are always allocated on the heap, or at least should be treated as if on the heap. 

## Thread Management

**What is the difference between *atomic* and *non-atomic* synthesized properties?**

First, properties are set to *atomic* by default. 

*Atomic* properties are more likely to guarentee thread-safety because it will ensure that a value is fully set (by the setter method) or fully retrieved (by the getter method) when accessor methods are called simultaneously.

*Non-atomic* properties, howeer are not thread-safe. While they run faster, they may cause race conditions. In the event that accessor methods are called simultaneously and a race condition occurs, a setter value would first release the old value and a getter method would retrieve nil since no value has not been set yet.

## Unit Testing

**What is the purpose of unit/UI testing? What are the benefits?**

Unit/UI testing are the basic of test-driven development. This development approach allows you to codify requirements for your code before you implement it. Unit tests are important to make sure that code meets its design and requirements and behaves as expected. Parts of the program are segregated and tested to ensure that individual parts are working correctly. 


