## Design patterns

### Links
[What’s a design pattern?](https://refactoring.guru/design-patterns/what-is-pattern)
[Why should I learn patterns?](https://refactoring.guru/design-patterns/why-learn-patterns)


### Questions

<details>
  <summary>What are design patterns?</summary>

  Design patterns are standard solutions to common problems in a software design. Each design pattern provides a customized blueprint for exacting problems. As a result, you cannot copy a pattern in your program, but you can use it as a design solution to your problem. The design patterns could be confused with algorithms because both concepts describe standard solutions to some known targets. But while an algorithm has always defined a clear set of actions, a pattern is a more high-level description of a solution.

</details>

<details>
  <summary>Why should patterns be learned?</summary>
  
  The truth is that a programmer can work without knowledge about patterns. Moreover, in this case, he can implement a pattern solution without knowing about it. So, why is it needed to learn them?

  There are a few reasons:

  1. Firstly, design patterns are a toolkit of solutions to common problems in software design. So, the programmer could solve problems using them.

	2. Secondly, design patterns are a common language that allows having more effective communication.

</details>

### Creational patterns

#### Links
[Factory Method](https://refactoring.guru/design-patterns/factory-method)
[Abstract Factory](https://refactoring.guru/design-patterns/abstract-factory)
[Builder](https://refactoring.guru/design-patterns/builder)
[Prototype](https://refactoring.guru/design-patterns/prototype)
[Singleton](https://refactoring.guru/design-patterns/singleton)

#### Questions

<details>
  <summary>What is Factory Method?</summary>

  Factory Method is a creational design pattern that provides an interface for creating objects in a superclass but allows subclasses to alter the type of created objects.

  Applicability:

  * Use the factory Method when beforehand unknown types and dependencies of the objects should work.
  * Use the Factory Method for providing users of your library or framework with a way to extend its internal components.
  * Use the Factory Method for saving system resources by reusing the existing exemplars instead of rebuilding them each time.

  Pros:

  * Avoid tight coupling between the creator and the concrete products.
  * Single Responsibility Principle. You can move the product creation code into one place in the program, making the code easier to support.
  * Open/Closed Principle. You can introduce new types of products into the program without breaking existing client code.

  Cons:

  * Each new subclass increases the code complexity. The best-case scenario is when introducing the pattern into an existing hierarchy of creator classes.

</details>

<details>
  <summary>What is Abstract Factory?</summary>

  Abstract Factory is a creational design pattern that lets you produce families of the related objects without specifying their concrete classes.

  Applicability:

  * Use the Abstract Factory when code needs to work with various families of related products but not to depend on the concrete classes of those products - they might be unknown beforehand or be simplified to allow for future extensibility.

  Pros:

  * Be sure that the products from a factory are compatible with each other.
  * Avoid tight coupling between concrete products and client code.
  * Single Responsibility Principle. Extract the product creation code into one place, making the code easier to support.
  * Open/Closed Principle. Introduce new variants of products without breaking existing client code.

  Cons:

  * Each new interface or class increases the complexity of the code.

</details>

<details>
  <summary>What is Builder?</summary>

  Builder is a creational design pattern that lets you construct complex objects step by step. The builder pattern allows producing different types and representations of an object using the same construction code.

  Applicability:

  * Use the Builder pattern to get rid of a 'telescopic constructor'.
  * Use the Builder pattern when an application needs to create different representations of some product, for example, stone and wooden houses.
  * Use the Builder to construct Composite trees or other complex objects.

  Pros:

  * Construct objects step-by-step, defer construction steps or run steps recursively.
  * Reuse the same construction code when building various representations of products.
  * Single Responsibility Principle. Isolate complex construction code from the business logic of the product.

  Cons:

  * The overall complexity of the code increases since the pattern requires creating multiple new classes.

</details>

<details>
  <summary>What is a Prototype?</summary>

  A Prototype is a creational design pattern that lets you copy existing objects without making your code dependent on their classes.

  Applicability:

  * Use the Prototype pattern when there isn't dependency from the concrete classes of copied objects in a code.
  * Use the pattern when you want to reduce the number of subclasses that only differ from the initialization of their respective objects. Somebody could have created these subclasses to be able to create a new one with a specific configuration.

  Pros:

  * Clone objects without coupling to their concrete classes.
  * Get rid of repeated initialization code in favour of cloning pre-built prototypes.
  * Produce complex exemplars more conveniently.
  * Get an alternative to inheritance when dealing with configuration presets.

  Cons:

  * Cloning complex objects that have circular references might be very tricky.

</details>

<details>
  <summary>What is Singleton?</summary>

  Singleton is a creational design pattern that lets you ensure that a class has only one instance while providing a global access point to this instance.

  Applicability:

  * Use the Singleton pattern when a class in your program should have just a single instance available to all clients; for example, a single database object shared by different parts of the program.
  * Use the Singleton pattern when you need stricter control over global variables.

  Pros:

  * You can be sure that a class has only a single instance.
  * You gain a global access point to that instance.
  * The initialization of the singleton object happens during the first call.

  Cons:

  * Single Responsibility Principle. The pattern solves two problems at the time.
  * The Singleton pattern can mask unluck design, for instance, when the program components know too much about each other.
  * The pattern requires special treatment in a multithreaded environment so that multiple threads cannot create a singleton object several times.
  * It may be difficult to unit test the client code because many test frameworks rely on inheritance when producing mock objects. Since the constructor of the singleton class is private and overriding static methods is impossible in most languages, you will need to think of a creative way to mock the singleton.

</details>

### Structural patterns

#### Links
[Adapter](https://refactoring.guru/design-patterns/adapter)
[Bridge](https://refactoring.guru/design-patterns/bridge)
[Composite](https://refactoring.guru/design-patterns/composite)
[Decorator](https://refactoring.guru/design-patterns/decorator)
[Facade](https://refactoring.guru/design-patterns/facade)
[Flyweight](https://refactoring.guru/design-patterns/flyweight)
[Proxy](https://refactoring.guru/design-patterns/proxy)

#### Questions

<details>
  <summary>What is Adapter?</summary>

  The adapter is a structural design pattern that allows objects with incompatible interfaces to collaborate.

  Applicability:

  * Use the adapter when you want to use some existing class, but its interface is not compatible with the rest of your code.
  * Use the pattern for reusing several existing subclasses that lack some functionality, and there is not possible to add it in the superclass.

  Prons:

  * Single Responsibility Principle. You can separate the interface or data conversion code from the primary business logic of the program.
  * Open/Closed Principle. You can introduce new types of adapters into the program without breaking the existing client code, as long as they work with the adapters through the client interface.

  Cons:

  * The overall complexity of the code increases because it requires introducing a set of new interfaces and classes. From time to time, changing into service is an easier way.

</details>

<details>
  <summary>What is Bridge?</summary>

  The Bridge is a structural design pattern that lets you split a large class or a set of closely related classes into two separate hierarchies - abstraction and implementation - their implementation independent of each other.

  Applicability:

  * Use the Bridge pattern when you want to divide and organize a class with several functional variants (for example, if the implemented class can work with various database servers).
  * Use the pattern when you need to extend a class in several orthogonal (independent) dimensions.
  * Use the Bridge if you need to be able to switch implementations at runtime.

  Prons:

  * You can create platform-independent classes and apps.
  * The client code works with high-level abstractions.
  * Open/Closed Principle. You can introduce new abstractions and implementations independently from each other.
  * Single Responsibility Principle. You can focus on high-level logic in the abstraction and on platform details in the implementation.

  Cons:

  * You might make the code more complicated by applying the pattern to a highly cohesive class.

</details>

<details>
  <summary>What is Composite?</summary>

  Composite is a structural design pattern that lets you compose objects into tree structures and then work with these structures as if they were individual objects.

  Applicability:

  * Use the Composite pattern when you have to implement a tree-like object structure.
  * Use it when you want the client code to treat both simple and complex elements uniformly.

  Prons:

  * It is possible to work with complex tree structures more conveniently: use polymorphism and recursion to your advantage.
  * Open/Closed Principle. You can introduce new element types into the app without breaking the existing code, which now works with the object tree.

  Cons:

  * It is difficult to provide a shared interface for classes whose functionality differs too much. In base scenarios, there is possible to overgeneralize the component interface, making it harder to comprehend.

</details>

<details>
  <summary>What is a Decorator?</summary>

  The decorator is a structural design pattern that lets you attach new behaviours to objects by placing these objects inside specialized wrapper objects that contain the behaviours.

  Applicability:

  * Use the Decorator pattern when it is possible to increase behaviours at runtime without breaking the code that uses these objects.
  * Use it when it is impossible to extend behaviour using inheritance.

  Prons:

  * It is possible to extend a behaviour without making a new subclass.
  * It is possible to add or remove responsibilities from an object at runtime.
  * It is possible to combine several behaviours by wrapping an object into multiple decorators.
  * Single Responsibility Principle. You can divide a monolithic class that implements many possible variants of behaviour into several smaller ones.

  Cons:

  * It is hard to remove a specific wrapper from the wrappers stack.
  * It is hard to implement a decorator with independent behaviour from the stack.
  * The initial configuration code of layers might look pretty ugly.

</details>

<details>
  <summary>What is a Facade?</summary>

  It is a structural design pattern that provides a simplified interface to a library, a framework, or any other complex set of classes.

  Applicability:

  * Use the Facade pattern when you need to have a limited but straightforward interface to a complex subsystem.
  * Use the Facade when you want to structure a subsystem into layers.

  Prons:

  * It is possible to isolate your code from the complexity of a subsystem.
  Cons:
  * A facade can become a god object coupled to all classes of an app.

</details>

<details>
  <summary>What is Flyweight?</summary>

  Flyweight is a structural design pattern that lets you fit more objects into the available amount of RAM by sharing common parts of the state between multiple exemplars instead of keeping all of the data in each object.

  Applicability:

  * Use the Flyweight pattern only when it is needed to optimize used RAM.

  Prons:

  * It is possible to save lots of RAM, assuming your program has tons of similar objects.

  Cons:

  * It is possible to trade RAM over CPU cycles when some context data needs recalculation each time somebody calls a flyweight method.
  * The code becomes much more complicated. New team members will always be wondering about the state.

</details>

<details>
  <summary>What is Proxy?</summary>

  Proxy is a structural design pattern that provides a substitute or placeholder for another object. A proxy controls access to the original one, allowing it to perform something either before or after the request gets through to the original one.

  Applicability:

  * Lazy initialization.
  * Access control (protection proxy).
  * Logging requests (logging proxy).
  * Caching request results (caching proxy).
  * Smart reference.

  Prons:

  * It is possible to control the service object without clients knowing about it.
  * It is possible to manage the lifecycle of the service object when clients do not care about it.
  * The proxy works even if the service object is not ready or is not available.
  * Open/Closed Principle. You can introduce new proxies without changing the service or clients.

  Cons:

  * The code may become more complicated since you need to introduce a lot of new classes.

</details>

### Behavioral patterns

#### Links
[Chain of responsibility](https://refactoring.guru/design-patterns/chain-of-responsibility)
[Command](https://refactoring.guru/design-patterns/command)
[Iterator](https://refactoring.guru/design-patterns/iterator)
[Mediator](https://refactoring.guru/design-patterns/mediator)
[Memento](https://refactoring.guru/design-patterns/memento)
[Observer](https://refactoring.guru/design-patterns/observer)
[State](https://refactoring.guru/design-patterns/state)
[Strategy](https://refactoring.guru/design-patterns/strategy)
[Template method](https://refactoring.guru/design-patterns/template-method)
[Visitor](https://refactoring.guru/design-patterns/visitor)

#### Questions

<details>
  <summary>What is Chain of Responsibility?</summary>

  Cin of Responsibility is a behavioural design pattern that lets you pass requests along a chain of handlers. Each handler decides thao process the request or move it on to the next handler in the chain.

  Applicability:

  * Use the Chain of Responsibility pattern when an expected program process different kinds of requests in various ways, but the exact types of requests and their sequences are unknown beforehand.
  * Use it when it is essential to execute several handlers in a particular order.
  * Use the CoR pattern when the set of handlers and their order are supposed to change at runtime.

  Prons:

  * You can control the order of request handling.
  * Single Responsibility Principle. It is possible to decouple classes that invoke operations from them.
  * Open/Closed Principle. You can introduce new handlers into the app without breaking the existing client code.

  Cons:

  * Some requests may end up unhandled.

</details>

<details>
  <summary>What is Command?</summary>

  It is a behavioural design pattern that turns a request into a stand-alone object that contains all information about it. This transformation lets you pass requests to method arguments, delay or queue a request execution, and support undoable operations.

  Applicability:

  * Use the Command pattern when you want to parametrize objects with operations.
  * Use the Command pattern when you want to queue operations, schedule their execution, or execute them remotely.
  * Use the Command pattern when an application can reverse operations.

  Prons:

  * Single Responsibility Principle. It is possible to decouple classes that invoke operations from them that perform these operations.
  * Open/Closed Principle. You can introduce new commands into the app without breaking existing client code.
  * You can implement undo/redo.
  * You can implement deferred execution of operations.
  * You can assemble a set of simple commands into a complex one.

  Cons:

  * The code may become more complicated since introducing a whole new layer between senders and receivers.

</details>

<details>
  <summary>What is Iterator?</summary>

  Iterator is a behavioural design pattern that lets you traverse elements of a collection without exposing its underlying representation (list, stack, tree, etc.).

  Applicability:

  * Use the Iterator pattern when element collection has a complex data structure under the hood, but you want to hide its complexity from clients (either for convenience or security reasons).
  * Use the pattern to reduce duplication of the traversal code across your app.
  * Use the Iterator when it is possible to traverse different data structures or when types of these structures are unknown beforehand.

  Prons:

  * Single Responsibility Principle. You can clean up the client code and the collections by extracting bulky traversal algorithms into separate classes.
  * Open/Closed Principle. You can implement new types of collections and iterators and pass them to existing code without breaking anything.
  * It is possible to iterate over the same collection in parallel because each iterative object contains its iteration state.
  * For the same reason, it is possible to delay an iteration and continue it when needed.

  Cons:

  * Applying the pattern can be overkill if your app only works with simple collections.
  * Using an iterator may be less efficient than going through elements of some specialized structure.

</details>

<details>
  <summary>What is Mediator?</summary>

  The Mediator is a behavioural design pattern that lets to reduce chaotic dependencies between objects. It restricts direct communications between exemplars and forces those to collaborate only via a mediator.

  Applicability:

  * Use the Mediator pattern when it is hard to change some of the classes.
  * Use it when it is possible to reuse a component in a different program.
  * Use the Mediator when you find yourself creating tons of component subclasses.

  Prons:

  * Single Responsibility Principle. It is possible to extract the communications between various components into a single place, making it easier to comprehend and maintain.
  * Open/Closed Principle. It is possible to introduce new mediators without having to change the components.
  * It is possible to reduce coupling between various components of a program.
  * It is possible to reuse individual components easier.

  Cons:

  * Over time a mediator can evolve into a God Object.

</details>

<details>
  <summary>What is Memento?</summary>

  Memento is a behavioural design pattern that lets you save and restore the previous state of an object without revealing the details of its implementation.

  Applicability:

  * Use the Memento pattern when you want to produce snapshots of the object state for the ability to restore a previous state of the object.
  * Use it when direct access to the object fields/getters/setters violates its encapsulation.

  Prons:

  * It is possible to produce snapshots of the state without violating its encapsulation.
  * It is possible to simplify the code by letting the caretaker maintain the history of the state.

  Cons:

  * The app might consume lots of RAM if clients create mementoes too often.
  * Caretakers should track the lifecycle to be able to destroy obsolete mementoes.
  * Most dynamic programming languages, such as PHP, Python and JavaScript, don't guarantee that the state within the Memento stays untouched.

</details>

<details>
  <summary>What is Observer?</summary>

  It is a behavioural design pattern that lets you define a subscription mechanism to notify multiple objects about any events.

  Applicability:

  * Use the Observer pattern when changes to the state of one object may require changing other ones, and the set of the object is unknown beforehand or changes dynamically.
  * Use the pattern when some parts in an app must observe others, but only for a limited time or in specific cases.

  Prons:

  * Open/Closed Principle. You can introduce new subscriber classes without changing the code (and vice versa if there is a publisher interface).
  * You can establish relations between objects at runtime.

  Cons:

  * Subscribers get notifications in random order.

</details>

<details>
  <summary>What is State?</summary>

  It is a behavioural design pattern that lets an object alter its behaviour when its internal state changes.

  Applicability:

  * Use the State pattern when you have an object that behaves differently depending on its current one, the number of states is enormous, and the state-specific code changes frequently.
  * Use the pattern when you have a class polluted with massive conditionals that alter how the class behaves according to the current values of the class fields.
  * Use State when you have a lot of duplicate code across similar states and transitions of a condition-based state machine.

  Prons:

  * Single Responsibility Principle. Organize the code related to particular states into separate classes.
  * Open/Closed Principle. Introduce new states without changing existing state classes or the context.
  * Simplify the code of the context by eliminating bulky state machine conditionals.

  Cons:

  * Applying the pattern can be overkill if a state machine has only a few states or rarely changes.

</details>

<details>
  <summary>What is Strategy?</summary>

  Strategy is a behavioural design pattern that lets you define a family of algorithms, but each of them into a separate class, and make their objects interchangeable.

  Applicability:

  * Use the Strategy pattern when you want to use different variants of an algorithm within an object and switch from one algorithm to another during runtime.
  * Use the Strategy when you have a lot of similar classes that only differ in executing some behaviour.
  * Use the pattern to isolate the business logic from the implementation details of algorithms that may not be as important.
  * Use it when your class has a massive conditional operator that switches between different variants of the same algorithm.

  Prons:

  * You can swap algorithms used inside an object at runtime.
  * You can isolate the implementation details of an algorithm from the code that uses it.
  * You can replace inheritance with composition.
  * Open/Closed Principle. You can introduce new strategies without having to change the context.

  Cons:

  * If you only have a couple of algorithms and they rarely change, there is no real reason to overcomplicate the program with new classes and interfaces that come along with the pattern.
  * Clients must be aware of the differences between strategies to be able to select a proper one.
  * Many modern programming languages have functional type support that lets you implement different versions of an algorithm inside a set of anonymous functions.

</details>

<details>
  <summary>What is the Template Method?</summary>

  Template Method is a behavioural design pattern that defines the skeleton of an algorithm in the superclass but lets subclasses override specific steps of the algorithm without changing its structure.

  Applicability:

  * Use the Template Method pattern when you want to let clients extend only steps of an algorithm, but not the whole algorithm or its structure.
  * Use the pattern when you have several classes that contain almost identical algorithms with some minor differences. As a result, you might need to modify all when the algorithm changes.

  Prons:

  * You can let clients override only certain parts of a large algorithm, making them less affected by changes into other parts of the algorithm.
  * You can pull the duplicate code into a superclass.

  Cons:

  * You might violate the Liskov Substitution Principle by suppressing a default step implementation via a subclass.
  Template methods tend to be harder to maintain the more steps they have.

</details>

<details>
  <summary>What is Visitor?</summary>

  It is a behavioural design pattern that lets you separate algorithms from the objects on which they operate.

  Applicability:

  * Use the Visitor when you need to operate on all elements of a complex object structure (for example, an object tree).
  * Use the Visitor to clean up the business logic of auxiliary behaviours.
  * Use the pattern when a behaviour makes sense only in some classes of a class hierarchy, but not in others.

  Prons:

  * Open/Closed Principle. You can introduce a new behaviour that can work with objects of different classes without changing these classes.
  * Single Responsibility Principle. You can move multiple versions of the same behaviour into the same class.
  * A visitor object can accumulate some information while working with various. It might be handy when you want to traverse some complex object structure, such as an object tree, and apply one to each object of this structure.

  Cons:

  * You need to update all visitors each time a class gets added to or removed from the element hierarchy.
  * Visitors might lack the necessary access to the private fields and methods of the elements

</details>
