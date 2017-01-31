# RFC 002- Framework Extensibility for Custom Assertions

## Summary
This details the MSTest V2 framework extensibility for extending the Assert class to add custom assertions.  

## Motivation
Often times, the default set of assertion APIs are not sufficient to satisfy a wide range of requirements for unit test writers. In most of these situations users end up having utility methods to address this need reducing discoverability in a test suite. If the test framework provides an extensibility in the assertion infrastructure itself, custom assertion functionality can be 
* Easily accessed
* Easily organized and 
* Possibly shared with the community.

## Detailed Design

### Requirements
1. Custom assertions should be easily pluggable into the test frameworks assertion infrastructure.
2. Users of custom assertions should be able to acquire and use them with ease.

### Proposed solution
 Here is a solution that is both easily pluggable and acquirable:

 The test frameworks Assertion class should be a non-static singleton with a C# Property('That') for accessing the instance:
 ```
    public class Assert{

        public static Assert That{
            get
            {
                ...
            }
        }
    }
 ```

Extension writers can then add C# extension methods for the Assertion class like below:
```
    public static class SampleAssertExtensions
    {
        public static void IsOfType<T>(this Assert assert, object obj)
        {
            if(obj is T)
            {
                return;
            }
            throw new AssertFailedException("Type does not match");
        }
    }
```

And consumers of this extension can consume it in their test code with the below simple syntax:
```
    using SampleAssertExtensionsNamespace;
    
    public void TestMethod
    {
        ...
        Assert.That.IsOfType<Dog>(animal);
    }
```

#### Benefits for custom assertion writers
1. Leverages the default C# constructs - No new interfaces/objects to understand and extend.
2. Extensions can be organized under a verb. For instance assertions expecting exceptions can be organized under the Throws verb like
```
Assert.That.Throws.InnerException
Assert.That.Throws.SystemException
Assert.That.Throws.ExceptionWithMessage
```

#### Benefits for custom assertion consumers
1. Easily discoverable - Intellisense shows up in most IDEs ensuring discoverability for these custom assertions since they are all rooted under the in-box Assert class.
2. Readable - Using linq type expressions enhances readability.