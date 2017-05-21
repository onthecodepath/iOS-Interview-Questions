# iOSInterviewConcepts
## Thread Management

**What is the difference between atomic and non-atomic synthesized properties?**

First, properties are set to atomic by default. 

Atomic properties are more likely to guarentee thread-safety because it will ensure that a value is fully set (by the setter method) or fully retrieved (by the getter method) when accessor methods are called simultaneously.

Non-atomic properties, howeer are not thread-safe. While they run faster, they may cause race conditions. In the event that accessor methods are called simultaneously and a race condition occurs, a setter value would first release the old value and a getter method would retrieve nil since no value has not been set yet.
