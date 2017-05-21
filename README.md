# iOS-Interview-Questions

A collection of iOS interview questions and answers in one place.

## Memory Management

**What is the difference between copy and retain?**

Calling retain on an object will increase its retain count by one. When the retain count of an objective reaches 0, the object will be deallocated and released from memory.

When you retain an object, you share the same version with whoever passed the object to you. But when you copy an object, you do not share the same version of the object that was passed to you. Instead, a duplicate of that object is created with duplicated values.

## Thread Management

**What is the difference between atomic and non-atomic synthesized properties?**

First, properties are set to atomic by default. 

Atomic properties are more likely to guarentee thread-safety because it will ensure that a value is fully set (by the setter method) or fully retrieved (by the getter method) when accessor methods are called simultaneously.

Non-atomic properties, howeer are not thread-safe. While they run faster, they may cause race conditions. In the event that accessor methods are called simultaneously and a race condition occurs, a setter value would first release the old value and a getter method would retrieve nil since no value has not been set yet.
