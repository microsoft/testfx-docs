# RFC 005- Framework Extensibility for Custom DataSource

## Summary
This details the MSTest V2 framework extensibility for specifying custom data source for data driven tests.

## Motivation
Often times, custom data sources are required for data driven tests. User should be able to leverage test framework extensibility to provide custom data sources for test execution.

## Detailed Design

### Requirements
1. A cusotm data source can be used by multiple test cases. 
2. A test case can have multiple data sources.

### Proposed solution
Here is a solution for using custom data source in data driven tests.

The test framework should define an interface `IDataSource` which can be extended to get data from custom data source.
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
```

```
    [TestMethod]
    [CustomTestDataSource]
    public void TestMethod1(int a, int b, int c)
    {
        
    }
```
In a similar way, multiple test methods can be decorated with same data source.
A test method can also be decorated with multiple data sources.

###  Discovery of `IDataSource` attributes
The MSTest v2 framework, on discovering a `TestMethod` probes additional attributes. On finding attributes inheriting from `IDataSource`, framework invokes `GetData()` to fetch test data and iteratively invokes test method with the test data as arguments.

### Benefits of using `IDataSource`
1. Users can extend `IDataSource` to support custom data sources.
2. Multiple tests can reuse the test data defined in same data source.
3. A test case can use multiple test data sources.
