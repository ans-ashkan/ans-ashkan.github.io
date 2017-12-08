# Design Pattens

## Creational

### Factory Class or Abstract Factory

Provide an interface for creating families of related or dependent objects without specifying their concrete classes.

Notes:  
This is usually used when we don't know required paramters of a class until runtime. e.g. injecting IFactory as paramter and using IFactory.Create(...) later when we know the parameters.

### Factory Method

Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.

This pattern is just like Abstract Factory, but without emphasis on familires.

Notes:  
usually used when we need multiple constructor overloads.
e.g. we add static methods with different paramters (but meaningful name) to the main class we are creating. (setting constructor to private is optional but recommended)

### Builder

Separate the construction of a complex object from its representation so that the same construction process can create different representations.

Notes:  
some people tend that StringBuilder class is an example of Builder pattern, but it isn't.

e.g. An IDocumentBuilder with methods such as AddTitle, AddParagraph, AddHeader and AddFooter may be implemented by multiple concrete classes such as TextDocumentBuilder, HtmlDocuementBuilder, MarkDownDocumentBuilder that creates multiple representation of IDocument.

### Prototype

Specify the kind of objects to create using a prototypical instance, and create new objects by copying this prototype.

Notes:  
In c# we have ICloneable providing Clone() method.

### Singleton

Ensure a class has only one instance and provide a global point of access to it.

Notes: 
In c# we can create a thread-safe singleton using a lock or by taking advantage of .net runtime, using a private static readonly member in conjuction with a get-only static property.

## Structural

### Adapter

Convert the interface of a class into another interface clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.

Wrap an existing class with a new interface.

Impedance match an old component to a new system

### Composite

Compose objects into tree structures to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects uniformly.

Notes:
HTML, XML, FileSystem are all possiblities of implementation using composite design pattern.  
e.g. HTML tags are all of type Tag with list of children of type Tag.

### Decorator

Attach additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.

Notes:  
Extend behaviour of a class without subclassing it for the sake of flexibility or maybe it's just a sealed/final class.

### Facade

Provide a unified interface to a set of interfaces in a subsystem. Façade defines a higher-level interface that makes the subsystem easier to use.

### Proxy

Provide a surrogate or placeholder for another object to control access to it.

Notes:  
e.g. a proxy that direct requests over network and returns responses, so it hides complexity of network but implements same interface as implementation on the server.

e.g. a proxy to use with IPC calls using shared memory.

Types: Remote Proxy, Virtual Proxy, Protection Proxy.

## Behavioral

### Command

Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.

Notes:  
ADO.NET uses command pattern.

### Observer

Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

Notes:  
We have a subject and multiple observers. Observers can be attached to or detached from subjects to update their states.

### Strategy

Define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients that use it.

Notes:  
We have ISortedList that it's sort algorithm is unkown to us, it can use QuickSort, MergeSort or ShellSort behind the scenes.

### Chain of Responsibility

Avoid coupling the sender of a request to its receiver by giving more than one object a chance to handle the request. Chain the receiving objects and pass the request along the chain until an object handles it.

## Resources

- [DoFactory](http://www.dofactory.com/net/)
- [SourceMaking](https://sourcemaking.com/design_patterns)