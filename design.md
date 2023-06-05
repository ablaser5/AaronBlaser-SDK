# SDK Design

The LordOfTheRings SDK utilizes several design patterns and principles that make 
using the SDK and extending it easy.

## Design Patterns

1. Facade Pattern: The LordOfTheRings class acts as a facade for API requests being made from the 
requests library. This pattern helps create a simple interface that can be used to access the Lord of the Rings API, 
making the client code of the SDK more readable and maintainable.

2. Factory Pattern: The Movie and Quotes classes can be seen as a loose interpretation of the factory pattern as 
the LordOfTheRings class acts as a factory that creates Movie and Quote objects. Using this methodology, this SDK
can also be extended to handle any other types of data the API may offer such as Characters, Chapters, and Books. 

3. Fluent Interface/Method Chaining: The ChainableMethods class allows for calling many methods in a single line, which
in the context of this SDK, makes using the api more readable and easier to use. 

## Design Principles

1. Composition: The APIResource class in the SDK is composed with the LordOfTheRings class to allow requests to be made with the 
Movie and Quote classes. Additionally, the Quotable class is composed with the Movie class to allow users to get quotes for a specific
type of data. This could be handy when trying to extend this functionality for something like a Character.

2. Single Responsibility: Each class in the SDK has a clear use. For example, the APIResource class represents a resource, or something
that would be requested from the API. The ChainableMethods class is responsible for handling parameters and building up the request. Then the 
LordOfTheRings class is responsible for making the requests.

3. Encapsulation: The APIResource class has the methods to get a single record as well as all records. New API resources can inherit from this
base class to add that functionality. 
 