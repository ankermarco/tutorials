# Learn Swift from Objective-C: Protocols and Delegation
## Protocols
in iOS development, a protocol is set of methods and properties that encapsulates a unit of functionality. The protocol doesn't actually contain any of the implementation for these things; it merely defines the required elements. Any class that declares itself to conform to this protocol must implement the methods and properties dictated in the protocol.

**1. Declaring a protocol**  

  _Objective-C_  
  In Objective-C, protocols are declared with the "@protocol" keyword. Below is an example of declaring a protocol containing one required method.
  ```
  @protocol SampleProtocol <NSObject>

  - (void)someMethod;

  @end
  ```
  _Swift_  
  In Swift, the syntax is a little different but the idea is the same.
  ```
  protocol SampleProtocol
  {
    func someMethod()
  }
  ```
**2. Conforming to a protocol**  

  _Objective-C_  
  In Objective-C, you add the protocol name in angle brackets beside the class interface declaration.

  MyClass is declaring that it conforms to SampleProtocol below. MyClass will also have to provide an implementation for "someMethod" in the implementation file because it is a required protocol method.
  ```
  MyClass.h

  @interface MyClass : NSObject<SampleProtocol>
  @end
  ```
  ```
  MyClass.m
  @implementation MyClass

  #pragma mark - SampleProtocol required method
  - (void)someMethod
  {
    NSLog('Hello world!');
  }

  @end
  ```
  _Swift_  
  In Swift, the protocol name is appended beside the superclass name, separated with a comma. If there isn't a superclass, then you just write a colon, followed by the protocol name.

  Example, both MyClass and AnotherClass conform to the SampleProtocol.
  ```
  class MyClass: SampleProtocol
  {
    // Conforming to SampleProtocol
    func someMethod() {
      // Do something here
    }
  }

  class AnotherClass: SomeSuperClass, SampleProtocol
  {
    // A subclass conforming to SampleProtocol
    func someMethod() {
      // Do something here
    }
  }
  ```

## Delegation

  Delegation works hand in hand with protocols because it allows a class to specify a delegate property which conforms to some protocol. Then a second class which actually conforms to that protocol can be assigned to that property. Now the first class can communicate with second class through the delegate property using the methods and properties as defined by the protocol.

  **1. Declaring a delegate property**

  _Objective-C_  

  In objective-C, declaring a delegate property involved using the "id" keyword as shown below.
  ```
  @interface FirstClass : NSObject

  @property (nonatomic, weak) id<SampleProtocol> delegate;

  @end
  ```
  _Swift_

  In Swift, declaring a delegate property is just like declaring any other property and you specify the protocol name as the type of the property.

  You may notice the question mark syntax which indicates that it's a property with an optional value (there may or may not be an object assigned to it).
  ```
  class FirstClass
  {
    var delegate:SampleProtocol?
  }
  ```
  **2. Calling a delegate method**

  _Objective-C_  

  In Objective-C, often times, you would see an if statement to check if there was an object assigned to the delegate property before calling the delegate method.
  ```
  if (self.delegate)
    [self.delegate someMethod];

  ```
  _Swift_

  In Swift, you can take advantage of the question mark syntax. If the delegate property is empty, nothing after the question mark will be executed.
  ```
  delegate?.someMethod()
  ```
