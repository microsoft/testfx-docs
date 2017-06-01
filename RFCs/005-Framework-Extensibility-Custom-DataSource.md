# RFC 005- Framework Extensibility for Custom DataSource

## Summary
This details the MSTest V2 framework extensibility for specifying custom data source for data driven tests.

## Motivation
Often times, custom data source is required for data driven tests. User should be able to leverage test framework extensibility to provide custom data sources for test execution.

## Detailed Design

### Requirements
1. Test data from custom data source should be easily associated with multiple test cases.

### Proposed solution
Here is a solution using which test data can be easily assocaited with test case.

The test framework should define an interface `IDataSource` which can be extended to get data from custom data source. The defintion of this interface is as below :
```
    public interface IDataSource
    {
        /// <summary>
        /// Gets the data from custom data source.
        /// </summary>
        public IEnumerable<object[]> GetData(MethodInfo methodInfo);
    }
```

Here is how the test methods are decorated with concrete implementation of `IDataSource`:
```
    public class CustomTestDataSourceAttribute : IDataSource, Attribute
    {
        public IEnumerable<object[]> GetData()
        {
            return new[]
                    {   new object[] {1, 2, 3},
                        new object[] {4, 5, 6}
                    };
        }
    }

    [TestMethod]
    [CustomTestDataSource]
    public void TestMethod1(int a, int b, int c)
    {
        
    }
```
In a similar way, multiple test methods can be decorated with same data source.

##  Discovery of `IDataSource` attributes
The MSTest v2 framework, on discovering a `TestMethod` probes additional attributes. On finding an attribute inheriting from `IDataSource`, framework invokes `GetData()` to fetch test data and iteratively invokes test method with the test data as arguments.

## Benefits of using `IDataSource`
1. Uses will be able to extend `IDataSource` to support custom data sources.
2. More than one tests can re-use the test data defined in same data source.

## Open questions
1. Should we support multiple `IDataSource` attributes for a single test method.
