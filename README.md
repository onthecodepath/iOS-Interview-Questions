# Hello fellow iOS Developers!

## What is this for?

Time is important. It's frustrating and time-consuming to have to search endlessly in order to practice iOS interview questions. The goal of this open-source project is to collect as many iOS interview questions together along with answers in order to save you time.

## Practice

Use the Table of Contents to practice and test your knowledge. It doesn't show the answer so you'll be able to go over the questions without relying on the answer for help.

## Table of Contents

- [Database](https://github.com/onthecodepath/iOS-Interview-Questions#database)
    - What is Core Data?
    - When would you use Core Data over NSUserDefault?
    - What is a managed object context?
    - What is NSFetchRequest?
- [Debugging](https://github.com/onthecodepath/iOS-Interview-Questions#debugging)
    - What are some ways of debugging in iOS?
- [Design Pattern](https://github.com/onthecodepath/iOS-Interview-Questions#design-patterns)
    - What is Singleton Pattern?
    - What is the delegation pattern?
    - What is MVC?
    - What is MVVM?
- [General / Uncategorized](https://github.com/onthecodepath/iOS-Interview-Questions#general--uncategorized)
    - What considerations do you need when writing a UITableViewController which shows images downloaded from a remote server?
    - What is a protocol? How do you define your own protocol? 
    - What is waterfall methodology and Agile methodology? What are the differences between them?
    - What is the difference between a class and an object?
    - What is JSON? What are the pros and cons?
    - What is the difference between not-running, inactive, active, background and suspended execution states?
    - Is it faster to iterate through an NSArray or an NSSet?
    - What is KVO?
- [Memory Management](https://github.com/onthecodepath/iOS-Interview-Questions#memory-management)
    - Why do you generally create a weak reference when using self in a block?
    - What is memory management handled on iOS?
    - What is the difference between *weak*, *strong* and *unowned*?
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
    - What is the difference between category and extension in Objective-C?
- [Swift](https://github.com/onthecodepath/iOS-Interview-Questions#swift)
    - What is the difference between public and open? Why is it important to have both?
    - What is the difference between var and let?
    - What is the difference between a struct and a class?
    - What is the difference between implicit and explicit?
- [Thread Management](https://github.com/onthecodepath/iOS-Interview-Questions#thread-management)
    - What is the difference between synchronous and asynchronous task?
    - What is the difference between atomic and non-atomic synthesized properties?
    - What is GCD and how is it used?
    - Explain the difference between Serial vs Concurrent.
- [Unit Testing / UI Testing](https://github.com/onthecodepath/iOS-Interview-Questions#unit-testing--ui-testing)
    - What is the purpose of unit testing? What are the benefits?
- [View / Storyboard](https://github.com/onthecodepath/iOS-Interview-Questions#view--storyboard)
    - What is the difference between viewDidLoad and viewDidAppear? Which should you use to load data from a remote server to display in the view?
    - What is the difference between frame and bound of a UIView?
    - What is the reuseIdentifier for?
    - What is autolayout?
- [Algorithm Resources](https://github.com/onthecodepath/iOS-Interview-Questions#algorithm-resources)
    - EKAlgorithm
    - swift-algorithm-club
- [Contributing](https://github.com/onthecodepath/iOS-Interview-Questions#contributing)
- [Thank You](https://github.com/onthecodepath/iOS-Interview-Questions#thank-you)
- [Flashcards](https://quizlet.com/serg_tsogtbaatar/folders/ios-interviews/sets)
    - The interview questions as flash card sets according to topic.

# Interview Questions & Answers


## Database

#### What is Core Data?

Core Data is a framework that is used to manage model layer objects. It has the ability to persist object graphs to a persistent store. Data is organized into relational entity-attribute model.

#### When would you use Core Data over NSUserDefault?

NSUserDefault is typically used to store small bits of data (settings, preferences, etc.). Core Data is used to store a large list of elements. 

#### What is a managed object context?

First, managed object context is an instance of NSManagedObjectContext. It is the central object in the Core Data stack. It is used to create and fetch managed objects, and to manage undo and redo operations. Although it is allowed to have multiple managed object contexts, there is typically at most one managed object to represent any given record in a persistent store.

#### What is NSFetchRequest?

NSFetchRequest is the class responsible for fetching from Core Data. Fetch requests can be used to fetch a set of objects meeting a certain criteria, individual values and more. ([source](https://medium.com/ios-os-x-development/50-ios-interview-questions-and-answers-part-2-45f952230b9f))

## Debugging

#### What are some ways of debugging in iOS?

- NSLog and print functions can be used for output into console.
- Breakpoints can also be used together with the Debug bar and Variables view as an alternative.
- Senior devs often use other tools such as Instruments and Crash Logs instead of the two above.

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

#### What considerations do you need when writing a UITableViewController which shows images downloaded from a remote server?

- Only download the image when the cell is scrolled into view (when cellForRowAtIndexPath is called)
- Download the image asynchronously on a background thread so as not to block the UI so the user can keep scrolling
- When the image has downloaded for a cell, check if that cell is still in the view or whether it has been re-used by another piece of data. If the cell has been re-used, then the image should be discarded. Otherwise, it should be switched back to the main thread to change the image on the cell. ([source](https://www.codementor.io/mattgoldspink/ios-interview-tips-questions-answers-objective-c-du1088nfb))

#### What is a protocol? How do you define your own protocol? 

A protocol defines a list of required and optional methods for a class that adopts the protocol to implement. Any class is allowed to implement a protocol so that other classes can send message to it based on the protocol methods without knowing the type of class. An example of how a protocol is defined:

<details open>
<summary>Objective-C</summary>
    
```objective-c
@protocol MyCustomDataSource
- (NSUInteger)numberOfRecords;
- (NSDictionary *)recordAtIndex:(NSUInteger)index;
@optional
- (NSString *)titleForRecordAtIndex:(NSUInteger)index;
@end
```
</details>

A common instance protocols are used is providing a DataSource for UITableView or UICollectionView ([source](https://www.codementor.io/mattgoldspink/ios-interview-tips-questions-answers-objective-c-du1088nfb))

#### What is waterfall methodology and Agile methodology? What are the differences between them?

Waterfall methodology is a sequential model for software development. It is separated into a sequence of pre-defined phases including feasibility, planning, design, build, test, production, and support.

On the other hand, Agile development methodology is a linear sequential apporach that provides flexibility for changing project requirements.

List of differences:
- Waterfall model divides software development process into different phases while Agile segregates the project development lifecycle into sprints. This makes waterfall more rigid while agile allows for more flexibility
- Waterfall model describes the software development life cycle as a single project while Agile considers it as a collection of many different projects; are iterations of different phases focusing on improving overall software quality with feedback from users and QA team.
- Since waterfall is more rigid, development requirements need to be clearly established beforehand since there is little flexibility for changing once project development starts. Meanwhile, Agile allow changes to be made anytime along the project development process even after initial planning has been completed.
- In Waterfall, the testing phase typically occurs after the build phase. In Agile, testing is often performed concurrently with programming or at least in the same iteration.
- Waterfall is more of an interal process that does not involve user feedback. Agile tends to involve user participation more in order to improve customer satisfaction.
- Waterfall model best fits projects that have a clearly defined set of requirements and where change to requirements is not expect. Agile fits more for projects where the requirements are expected to change and evolve.
- Waterfall can exhibit a project mindset that focuses on completion of the project while Agile can allow for more focus on developing a product that satisfies customers.

#### What is the difference between a class and an object?

In the simplest sense, a class is a blueprint for an object. It describes the properties and behaviors common to any particular type of object. An object, on the other hand, is an instance of a class.

#### What is JSON? What are the pros and cons?

JSON stands for JavaScript Object Notation. According to [wiki](https://en.wikipedia.org/wiki/JSON), it is a file format that uses human-readable text to transmite data objects consisting of attribute-value pairs and array data types. 

Pros:

- It is lighter than XML meaning that it can represent the same data in XML in fewer bytes. This makes network transmissions and read/writes faster
- Since it is native to JavaScript, computationally-expensive XSL tranformations are not needed in order to extract data

Cons:

- Not as widespread as XML
- Data is not readily streamable and has to be broken up into individual objects
- Can't use comments

#### What is the difference between not-running, inactive, active, background and suspended execution states?

- **Not-running state** occurs when the app either has not be launched or was running but was terminated by the system.
- **Inactive state** occurs where the app runs in the foreground but is currently not receiving events. (It may be executing other code though). This state is typically brief as apps transitions to other states.
- **Active state** is where the app is running in the foreground and receiving events. This is the normal mode for foreground apps.
- **Background state** occurs when the app is in the background and executing code. Apps typically enter this state on their way to being suspended. Apps that require extra execution time may remain in this screen longer. Apps being launched directly into the background enters this state instead of inactive state.
- **Suspended state** is where the app is in the background but it is not executing code. Apps will remain in memory, but are removed by the system if low-memory condition occurs in order to make more space for foreground apps.

#### Is it faster to search for an item in an NSArray or an NSSet?

It depends. NSSet is faster to lookup an item in but can hold at most one of any given object. The reason is because NSSet uses hash values in order to find items. NSArray can hold multiple copies of an object but is slower to search for an item as it has to iterate through its entire contents to find it. ([source - #25](https://medium.com/cocoaacademymag/25-ios-interview-questions-and-answers-for-junior-developers-19bfe6e99b0))

#### What is KVO?

KVO stands for *Key-Value Observing*. It allows a controller or class to *observe* when a property value changes. 

## Memory Management

#### Why do you generally create a weak reference when using self in a block?

Sometimes it is necessary it capture self in a block such as when defining a callback block. However, since blocks maintain strong references to any captured objects including self, this may lead to a strong reference cycle and memory leak.

Instead, capturing a weak reference to self is recommended in order to avoid this issue:

<details open>
<summary>Objective-C</summary>

```objective-c
SomeBlock* __weak weakSelf = self;
```
</details>


#### What is memory management handled on iOS?

iOS uses something called ARC which stands for Automatic Reference Counting. When an object is said to have a strong reference to it, ARC increase its retain count by 1. When the retain count of an object reaches 0, the object will typically be deallocated if there are no more strong references to it. Unlike garbage collection, ARC does not handle reference cycles automatically. 

#### What is the difference between *weak*, *strong* and *unowned*?

First, objects are *strong* by default.

- *Strong* means that the reference count will be increased and the reference to it will be maintained through the life of the object. 
- *Weak*, means that we are pointing to an object but not increasing its reference count. It's always optional. It’s often used when creating a parent child relationship. The parent has a strong reference to the child but the child only has a weak reference to the parent. ([source](https://medium.com/ios-os-x-development/ios-interview-questions-13840247a57a))
- *Unowned* is the same as *Weak* in terms of reference counting but *Unowned* can be non-optional. It's useful when you are sure the object will not be accessed when it's nil (in this case it would cause an Error) because *Unowned* references don't require nil checking.

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

*Synthesize* generates getter and setter methods for your property.

#### What is dynamic in Objective-C?

Dynamic is used for subclasses of NSManagedObject. @dynamic can also be used to delegate the responsibility of implementing the accessors. ([source](https://medium.com/ios-os-x-development/ios-interview-questions-13840247a57a))

#### What is the difference between _ vs self. in Objective-C?

You typically use either when accessing a property in Objective-C. When you use _, you're referencing the actual instance variable directly. You should avoid this. Instead, you should use self. to ensure that any getter/setter actions are honored. 

In the case that you would write your own setter method, using _ would not call that setter method. Using self. on the property, however, would call the setter method you implemented. 

#### What are blocks in Objective-C?

Blocks are a language-level feature of Objective (C and C++ too). They are objects that allow you to create distinct segments of code that can be passed around to methods or functions as if they were values. This means that a block is capable of being added to collections such as NSArray or NSDictionary. Blocks are also able to take arguments and return values similar to methods and functions.

The syntax to define a block literal uses the caret symbol(^):

<details open>
<summary>Objective-C</summary>
    
```objective-c
^{
  NSLog(@"This is an example of a block")
}
```
</details>

#### What is the difference between category and extension in Objective-C?

A category and extension are similar in functionality where they can add additional instance and class methods to a class. However, an extension can only do so if the source code for the class being extended is available at compile time. This means that classes such as NSString cannot be extended. Instead, a category would be used to add additional methods to the NSString class

## Swift

#### What is the difference between public and open? Why is it important to have both?

Open access imposes limitations on class inheritance. Classes declared with open level access can be subclassed by modules they are defined in, modules that import the module in which the class is defined, and class members as well. While this sounds similar to the public access level defined in Swift 2, there is a small difference. In Swift 3, the meaning of public access level means that classes declared public can only be subclassed in the module they are defined in. This includes public class members which can be overridden by subclasses defined int he module they are defined in.

Some classes of libraries and frameworks are not designed to be subclasses. For example, in the Core Data framework, Apple states that some methods of NSManagedObject should not be overridden. To prevent any unexpected behavior that may result from overriding those methods, Apple declares those methods public rather than open. As a result, those methods are not marked as open for developers to override. ([source](https://cocoacasts.com/what-is-the-difference-between-public-and-open-in-swift-3/))

#### What is the difference between *var* and *let*?

*var* is a variable that can be changed while *let* denotes a constant that cannot be changed once set.

#### What is the difference between a struct and a class?

The main difference to note is that structs are value types (stored on stack) while classes are reference types (stored on heap). 

Classes have capabilities that structs do not:
- Inheritance enables one class to inherit the characteristics of another. ([source](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/ClassesAndStructures.html))
- Type casting enables you to check and interpret the type of a class instance at runtime.
- Deinitializers enable an instance of a class to free up any resources it has assigned.
- Reference counting allows more than one reference to a class instance.

#### What is the difference between implicit and explicit?

When referring to something as implicit or explicit, it is often referring to how an object is declared. In the two examples below:

<details open>
<summary>Swift</summary>
    
```swift
var name: String = "onthecodepath" // explicit
var name = "onthecodepath" // implicit
```
</details>

In the first line above, the name variable is *explicitly* declared since the type of the variable follows the name of the variable. In the second line, the String type is not explicitly declared. However, Swift is able to infer that name is of a String type since the value that it is being set as is of a String type.

## Thread Management

#### What is the difference between synchronous and asynchronous task?

Synchronous tasks wait until the task has been completed while asynchronous tasks can run in the background and send a notification when the task is complete.

#### What is the difference between *atomic* and *non-atomic* synthesized properties?

First, properties are set to *atomic* by default. 

*Atomic* properties are more likely to guarentee thread-safety because it will ensure that a value is fully set (by the setter method) or fully retrieved (by the getter method) when accessor methods are called simultaneously.

*Non-atomic* properties, however are not thread-safe. While they run faster, they may cause race conditions. In the event that accessor methods are called simultaneously and a race condition occurs, a setter value would first release the old value and a getter method would retrieve nil since no value has not been set yet.

#### What is GCD and how is it used?

GCD stands for Grand Central Dispatch. According to [Ray Wenderlich](https://www.raywenderlich.com/60749/grand-central-dispatch-in-depth-part-1), it offers the following benefits
- Improving your app's responsiveness by helping to defer computationally expensive tasks and run them in the background.
- Providing an easier concurrency model than locks and threads and helps to avoid concurrency bugs.
- Potentially optimize your code with higher performance primitives for common patterns such as singletons.

In other words, GCD provides and manages queues of tasks in the iOS app. This is one of the most commonly used API to manage concurrent code and execute operations asynchronously. Network calls are often performed on a background thread while things like UI updates are executed on the main thread.

#### Explain the difference between Serial vs Concurrent

Tasks executed *serially* are executed one at a time while tasks that are executed *concurrently* may be executed at the same time.

#### Spot the bug that occurs in the code:

<details open>
<summary>Swift</summary>

```swift
class ViewController: UIViewController {
    @IBOutlet var alert: UILabel!
    override func viewDidLoad() {
        super.viewDidLoad()
        let frame: CGRect = CGRect(x: 100, y: 100, width: 100, height: 50)
        self.alert = UILabel(frame: frame)
        self.alert.text = "Please wait..."
        self.view.addSubview(self.alert)
    }
    DispatchQueue.global(qos: .default).async {
        sleep(10)
        self.alert.text = "Waiting over"
    }
}
```
</details>

<details>
<summary>Objective-C</summary>

```objective-c
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
</details>
<br>

All UI updates must be performed on the main thread. Global dispatch queues do not make any guarantees so code should be modified to run the UI update on the main thread. Here is the fix below:


<details open>
<summary>Swift</summary>

```swift
DispatchQueue.global(qos: .default).async {
    sleep(10)
    DispatchQueue.main.async {
        self.alert.text = "Waiting over"
    }
}
```
</details>

<details>
<summary>Objective-C</summary>
    
```
dispatch_async(		
dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0),
^{
    sleep(10);
    dispatch_async(dispatch_get_main_queue(), ^{
        self.alert.text = @"Waiting over";
    });
}); 

```
</details>

## Unit Testing / UI Testing

#### What is the purpose of unit/UI testing? What are the benefits?

Unit/UI testing are the basic of test-driven development. This development approach allows you to codify requirements for your code before you implement it. Unit tests are important to make sure that code meets its design and requirements and behaves as expected. Parts of the program are segregated and tested to ensure that individual parts are working correctly. 

## View / Storyboard

#### What is the difference between viewDidLoad and viewDidAppear? Which should you use to load data from a remote server to display in the view?

viewDidLoad is only called when the view is loaded (after loadView is called). viewDidAppear, on the other hand, is called everytime the view appears on the device. 

If the data is static for the most part, it can be loaded in viewDidLoad and cached. But if the data is dynamic and likely to change often, it is preferrable to use viewDidAppear. In both instances, data should be loaded asynchronously on a background thread to avoid blocking the UI.

#### What is the difference between frame and bound of a UIView?

The *frame* of a UIView is the region relative to the superview it is contained within while the *bounds* of a UIView is the region relative to its own coordinate system.

#### What is the reuseIdentifier for?

The *reuseIdentifier* indicates that cells for a UITableView (or UICollectionView) can be reused. UITableView maintains an internal cache of UITableViewCell with the appropriate identifier and allows them to be reused when dequeueForCellWithReuseIdentifier is called. As a result, this increases performance of UITableView since a new view does not have to be created for a cell.

#### What is Auto Layout?

Auto Layout is used to dynamically calculate the size and position of views based on constraints.

# Algorithm Resources

#### [EKAlgorithm](https://github.com/EvgenyKarkan/EKAlgorithms): Algorithm and data structures in Objc

#### [swift-algorithm-club](https://github.com/raywenderlich/swift-algorithm-club): Algorithm and data structures in Swift

# Contributing

#### There's a typo / an incorrect answer to one of your questions

Great! Creating an issue will let me know what changes should be made. You can even making the changes yourself and make a pull request which will expedite the process!

#### Requesting questions to be answered and topics

If you open an issue, I would be happy to go ahead and add the question with the appropriate answer when I get to it!

# Thank You

#### Contributors

- onthecodePath
- Sergtsaeb









