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

The test framework should define an abstract class `DataSource` which can be extended to get data from custom data source.
```
    public abstract DataSource : Attribute
    {
        /// <summary>
        /// Gets the test data from custom data source.
        /// </summary>
        public abstract IEnumerable<object[]> GetData(MethodInfo methodInfo);

        /// <summary>
        /// Display name to be displayed for test corresponding to data row.
        /// </summary>
        public virtual string GetDisplayName(MethodInfo methodInfo, object[] data);
    }
```

Here is how the test methods are decorated with concrete implementation of `DataSource`:
```
    public class CustomTestDataSourceAttribute : DataSource
    {
        public IEnumerable<object[]> GetData(MethodInfo methodInfo)
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

###  Discovery of `DataSource` attributes
The MSTest v2 framework, on discovering a `TestMethod` probes additional attributes. On finding attributes inheriting from `IDataSource`, framework invokes `GetData()` to fetch test data and iteratively invokes test method with the test data as arguments.

### Benefits of using `DataSource`
1. Users can extend `DataSource` to support custom data sources.
2. Multiple tests can reuse the test data defined in same data source.
3. A test case can use multiple test data sources.
