# Hello fellow iOS Developers!

## What is this for?

Time is important. It's frustrating and time-consuming to have to search endlessly in order to practice iOS interview questions. The goal of this open-source project is to collect as many iOS interview questions together along with answers in order to save you time.

## Practice

Use the Table of Contents to practice and test your knowledge. It doesn't show the answer so you'll be able to go over the questions without relying on the answer for help.

## Table of Contents

- [Database](https://github.com/onthecodepath/iOS-Interview-Questions#core-data)
    - What is Core Data?
    - When would you use Core Data over NSUserDefault?
    - What is a managed object context?
- [Debugging](https://github.com/onthecodepath/iOS-Interview-Questions#debugging)
- [Design Pattern](https://github.com/onthecodepath/iOS-Interview-Questions#design-patterns)
    - What is Singleton Pattern?
    - What is the delegation pattern?
    - What is MVC?
    - What is MVVM?
- [General / Uncategorized](https://github.com/onthecodepath/iOS-Interview-Questions#general--uncategorized)
    - What is the difference between a class and an object?
    - What is JSON?
    - What is the difference between not-running, inactive, active, background and suspended execution states?
    - Is it faster to iterate through an NSArray or an NSSet?
    - What is KVO?
- [Memory / Memory Management](https://github.com/onthecodepath/iOS-Interview-Questions#memory--memory-management)
    - What is memory management handled on iOS?
    - What is the difference between *weak* and *strong*?
    - What is a memory leak?
    - What is a retain cycle?
    - What is the difference between copy and retain?
    - What is the difference between a stack vs a heap?
- [Networking](https://github.com/onthecodepath/iOS-Interview-Questions#networking)
- [Objective-C](https://github.com/onthecodepath/iOS-Interview-Questions#objective-c)
    - What is synthesize in Objective-C?
    - What is dynamic in Objective-C?
    - What is the difference between _name vs self.name?
    - What are blocks in Objective-C?
    - What is the difference between category and extension in Objective-c?
- [Swift](https://github.com/onthecodepath/iOS-Interview-Questions#swift)
    - What is the difference between var and let?
    - What is the difference between a struct and a class?
    - What is the difference between implicit and explicit?
- [Thread Management](https://github.com/onthecodepath/iOS-Interview-Questions#thread-management)
    - What is the difference between atomic and non-atomic synthesized properties?
    - What is the difference between a stack vs a heap?
    - What is GCD?
    - Explain the difference between Serial vs Concurrent.
- [Unit Testing / UI Testing](https://github.com/onthecodepath/iOS-Interview-Questions#unit-testing--ui-testing)
    - What is the purpose of unit testing? What are the benefits?
- [View / Storyboard](https://github.com/onthecodepath/iOS-Interview-Questions#view--storyboard)
    - What is the difference between frame and bound of a UIView?
    - What is the reuseIdentifier for?
- [Algorithm Resources](https://github.com/onthecodepath/iOS-Interview-Questions#algorithm-resources)
    - EKAlgorithm
    - swift-algorithm-club
- [Contributing](https://github.com/onthecodepath/iOS-Interview-Questions#contributing)

# Interview Questions

## Database

#### What is Core Data?

In Apple's [words](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CoreData/index.html?utm_source=iosstash.io), "Core Data is a framework that you use to manage the model layer objects in your application. It provides generalized and automated solutions to common tasks associated with object life cycle and object graph management, including persistence."

#### When would you use Core Data over NSUserDefault?

NSUserDefault is typically used to store small bits of data (settings, preferences, etc.). Core Data is used to store a large list of elements. 

#### What is a managed object context?

First, managed object context is an instance of NSManagedObjectContext. It is the central object in the Core Data stack. It is used to create and fetch managed objects, and to manage undo and redo operations. Although it is allowed to have multiple managed object contexts, there is typically at most one managed object to represent any given record in a persistent store.

## Debugging

## Design Patterns

#### What is Singleton Pattern?

The Singleton design pattern ensures that only one instance exists for a given class and that there’s a global access point to that instance. It usually uses lazy loading to create the single instance when it’s needed the first time. ([source](https://medium.com/ios-os-x-development/ios-interview-questions-13840247a57a))

#### What is the delegation pattern? 

The delegation pattern is a powerful pattern used in building iOS applications. The basic idea is that one object will act on another object's behalf or in coordination with another object. The delegating object typically keeps a reference to the other object (delegate) and sends a message to it at the appropriate time. It is important to note that they have a one to one relationship.

#### What is MVC?

MVC stands for **Model-View-Controller**. It is a software architecture pattern for implementing user interfaces. 

MVC consists of three layers: the model, the view, and the controller.
- The **model layer** is typically where the data resides (persistence, model objects, etc)
- The **view layer** is typically where all the UI interface lies. Things like displaying buttons and numbers belong in the view layer. The view layer does not know anything about the model layer and vice versa.
- The **controller (view controller)** is the layer that integrates the view layer and the model layer together. 

#### What is MVVM?

MVVM stands for **Model-View-ViewModel**. It is a software architecture pattern for implementing user interfaces.

MVVM is an augmented version of MVC where the presentation logic is moved out of the controller and into the view model. The view model is responsible for handling most, if not all, of the view's display logic. 

A common occurence in MVC is where you have a massive-view-controller (some joke this is what MVC stands for). In order to shrink the size of your view controller and make the logic and readibility of your code easier to follow along, the MVVM will be used. 

## General / Uncategorized

#### What is the difference between a class and an object?

In the simplest sense, a class is a blueprint for an object. It describes the properties and behaviors common to any particular type of object. An object, on the other hand, is an instance of a class.

#### What is JSON?

JSON stands for JavaScript Object Notation. According to [wiki](https://en.wikipedia.org/wiki/JSON), it is a file format that uses human-readable text to transmite data objects consisting of attribute-value pairs and array data types. 

#### What is the difference between not-running, inactive, active, background and suspended execution states?**

- Not-running occurs when the app either has not be launched or was running but was terminated by the system.
- Inactive occurs where the app runs in the foreground but is currently not receiving events. (It can possibly be executing other code though). This state is typically brief as apps transitions to other states.
- Active state is where the app is running in the foreground and receiving events. This is the normal mode for foreground apps.
- Background state is where the app is in the background and executing code. Apps typically enter this state on their way to being suspended. Apps that require extra execution time may remain in this screen longer. Apps being launched directly into the background enters this state instead of inactive state.
- Suspended state is where the app is in the background but it is not executing code. Apps will remain in memory, but are removed by the system if low-memory condition occurs in order to make more space for foreground apps.

#### Is it faster to iterate through an NSArray or an NSSet?

It depends. NSSet is faster to iterate through if the order of the items in the collection is not important. The reason is because NSSet uses hash values in order to find items while NSArray has to iterate through its entire contents to find a particular object. ([source - #25](https://medium.com/cocoaacademymag/25-ios-interview-questions-and-answers-for-junior-developers-19bfe6e99b0))

#### What is KVO?

KVO stands for *Key-Value Observing*. It allows a controller or class to *observe* when a property value changes. 

## Memory / Memory Management

#### What is memory management handled on iOS?

iOS uses something called ARC which stands for Automatic Reference Counting. When an object is said to have a strong reference to it, ARC increase its retain count by 1. When the retain count of an object reaches 0, the object will typically be deallocated if there are no more strong references to it. Unlike garbage collection, ARC does not handle reference cycles automatically. 

#### What is the difference between *weak* and *strong*?

First, objects are *strong* by default.

- *Strong* means that the reference count will be increased and the reference to it will be maintained through the life of the object. 
- *Weak*, means that we are pointing to an object but not increasing its reference count. It’s often used when creating a parent child relationship. The parent has a strong reference to the child but the child only has a weak reference to the parent. ([source](https://medium.com/ios-os-x-development/ios-interview-questions-13840247a57a))

Common instances of *weak* references are delegate properties and subview/controls of a view controller's main view since those views are already strongly held by the main view. ([source](http://stackoverflow.com/questions/11013587/differences-between-strong-and-weak-in-objective-c))

#### What is a memory leak?

A memory leak commonly occurs when an object is allocated in such a way that when it is no longer in use or needed, it is not released. In iOS programming, you create certain objects with weak references in order to avoid a strong to strong relationship that creates a retain cycle and a memory leak.

#### What is a retain cycle?

Retain cycles can occur when memory management is based on retain count. This typically occurs when two objects strongly reference each other. As a result, the retain count of either object will never reach zero and deallocated from memory (hence retaining each other). 

#### What is the difference between *copy* and *retain*?

Calling *retain* on an object will increase its *retain* count by one. When the *retain* count of an objective reaches 0, the object will be deallocated and released from memory.

When you *retain* an object, you share the same version with whoever passed the object to you. But when you *copy* an object, you do not share the same version of the object that was passed to you. Instead, a duplicate of that object is created with duplicated values.

#### What is the difference between a stack vs a heap?

A stack is a region of memory where data is added or removed in a last-in-first-out (LIFO) order. According to [Ates Goral](http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap), it is the memory set aside as scratch space for a thread of execution. Meanwhile the heap is memory set aside for dynamic allocation. Unlike the stack, you can allocate a block at any time and free it at anytime. 

Note: In Objective-C, all objects are always allocated on the heap, or at least should be treated as if on the heap. 

## Networking

## Objective-C

#### What is synthesize in Objective-C?

The method synthesize generates getter and setter methods for your property.

#### What is dynamic in Objective-C?

Dynamic is used for subclasses of NSManagedObject. @dynamic can also be used to delegate the responsibility of implementing the accessors. ([source](https://medium.com/ios-os-x-development/ios-interview-questions-13840247a57a))

#### What is the difference between _ vs self. in Objective-C?

You typically use either when accessing a property in Objective-C. When you use _, you're referencing the actual instance variable directly. You should avoid this. Instead, you should use self. to ensure that any getter/setter actions are honored. 

In the case that you would write your own setter method, using _ would not call that setter method. Using self. on the property, however, would call the setter method you implemented. 

#### What are blocks in Objective-C?

Blocks are a language-level feature of Objective (C and C++ too). They are objects that allow you to create distinct segments of code that can be passed around to methods or functions as if they were values. This means that a block is capable of being added to collections such as NSArray or NSDictionary. Blocks are also able to take arguments and return values similar to methods and functions.

The syntax to define a block literal uses the caret symbol(^):

```
^{
  NSLog(@"This is an example of a block"
}
```

#### What is the difference between category and extension in Objective-c?

A category and extension are similar in functionality where they can add additional instance and class methods to a class. However, an extension can only do so if the source code for the class being extended is available at compile time. This means that classes such as NSString cannot be extended. Instead, a category would be used to add additional methods to the NSString class

## Swift

#### What is the difference between *var* and *let*?

*var* is a variable that can be changed while *let* denotes a constant that cannot be changed once set.

#### What is the difference between a struct and a class?

Structs are value types while classes are reference types. Classes have capabilities that structs do not:
- Inheritance enables one class to inherit the characteristics of another. ([source](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/ClassesAndStructures.html))
- Type casting enables you to check and interpret the type of a class instance at runtime.
- Deinitializers enable an instance of a class to free up any resources it has assigned.
- Reference counting allows more than one reference to a class instance.

#### What is the difference between implicit and explicit?

When referring to something as implicit or explicit, it is often referring to how an object is declared. In the two examples below:

```
var name: String = "onthecodepath" // explicit
var name = "onthecodepath" // implicit
```

In the first line above, the name variable is *explicitly* declared since the type of the variable follows the name of the variable. In the second line, the String type is not explicitly declared. However, Swift is able to infer that name is of a String type since the value that it is being set as is of a String type.

## Thread Management

#### What is the difference between *atomic* and *non-atomic* synthesized properties?

First, properties are set to *atomic* by default. 

*Atomic* properties are more likely to guarentee thread-safety because it will ensure that a value is fully set (by the setter method) or fully retrieved (by the getter method) when accessor methods are called simultaneously.

*Non-atomic* properties, howeer are not thread-safe. While they run faster, they may cause race conditions. In the event that accessor methods are called simultaneously and a race condition occurs, a setter value would first release the old value and a getter method would retrieve nil since no value has not been set yet.

#### What is GCD?

GCD stands for Grand Central Dispatch. According to [Ray Wenderlich](https://www.raywenderlich.com/60749/grand-central-dispatch-in-depth-part-1), it offers the following benefits
- Improving your app's responsiveness by helping to defer computationally expensive tasks and run them in the background.
- Providing an easier concurrency model than locks and threads and helps to avoid concurrency bugs.
- Potentially optimize your code with higher performance primitives for common patterns such as singletons.

#### Explain the difference between Serial vs Concurrent

Tasks executed *serially* are executed one at a time while tasks that are executed *concurrently* may be executed at the same time.

#### Spot the bug that occurs in the code:

```
@interface MyCustomController : UIViewController  

@property (strong, nonatomic) UILabel *alert;  

@end  

@implementation MyCustomController  

- (void)viewDidLoad {
  CGRect frame = CGRectMake(100, 100, 100, 50);
  self.alert = [[UILabel alloc] initWithFrame:frame];
  self.alert.text = @"Please wait...";
  [self.view addSubview:self.alert];
  dispatch_async(
    dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0),
    ^{
      sleep(10);
      self.alert.text = @"Waiting over";
    }
  ); 
}  
```

All UI updates must be performed on the main thread. Global dispatch queues do not make any guarantees so code should be modified to run the UI update on the main thread. 

## Unit Testing / UI Testing

#### What is the purpose of unit/UI testing? What are the benefits?

Unit/UI testing are the basic of test-driven development. This development approach allows you to codify requirements for your code before you implement it. Unit tests are important to make sure that code meets its design and requirements and behaves as expected. Parts of the program are segregated and tested to ensure that individual parts are working correctly. 

## View / Storyboard

#### What is the difference between frame and bound of a UIView?

The *frame* of a UIView is the region relative to the superview it is contained within while the *bounds* of a UIView is the region relative to its own coordinate system.

#### What is the reuseIdentifier for?

The *reuseIdentifier* indicates that cells for a UITableView (or UICollectionView) can be reused. UITableView maintains an internal cache of UITableViewCell with the appropriate identifier and allows them to be reused when dequeueForCellWithReuseIdentifier is called. As a result, this increases performance of UITableView since a new view does not have to be created for a cell.

# Algorithm Resources

#### [EKAlgorithm](https://github.com/EvgenyKarkan/EKAlgorithms): Algorithm and data structures in Objc

#### [swift-algorithm-club](https://github.com/raywenderlich/swift-algorithm-club): Algorithm and data structures in Swift

# Contributing

#### There's a typo / an incorrect answer to one of your questions

Great! Creating an issue will let me know what changes should be made. You can even making the changes yourself and make a pull request which will expedite the process!

#### Requesting questions to be answered and topics

If you open an issue, I would be happy to go ahead and add the question with the appropriate answer when I get to it!








