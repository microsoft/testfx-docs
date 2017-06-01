# RFC 006- DynamicData Attribute for Data Driven Tests

## Summary
This details the MSTest V2 framework attribute "DynamicData" for data driven tests where test data, declared as properties or methods, can be shared between more than one test cases.

## Motivation
Often times, the inline test data need to be shared between tests. There could be more than one test cases in different files which can use same test data. In most of these situations, user end up declaring same inline data for multiple test cases using "DataRow" attribute. Test framework should provide feature so that test data, declared as property, can be
* Easily re-used
* Easily organized

## Detailed Design

### Requirements
1. Inline test data can be reused by multiple test cases.

### Proposed solution
Here is a solution that meets the above requirements:

The property storing test data should be declared as static.
```
[TestClass]
public class UnitTests
{
    static IEnumerable<object[]> ReusableTestDataProperty
        {
            get
            {
                return new[]
                    {   new object[] {1, 2, 3},
                        new object[] {4, 5, 6}
                    };
            }
        }

    static IEnumerable<object[]> ReusableTestDataMethod()
    {
        return new[]
                    {   new object[] {1, 2, 3},
                        new object[] {4, 5, 6}
                    }; 
    }

    // Property ReusableTestDataProperty can be used to associate test data with data driven test case like below:
    [TestMethod]
    [DynamicData("ReusableTestDataProperty")]
    public void DynamicDataTestMethod1(int a, int b, int c)
    {
        Assert.IsTrue(1, a%3);
        Assert.IsTrue(2, b%3);
        Assert.IsTrue(0, c%3);
    }

    // Method ReusableTestDataMethod can be used to associate test data with data driven test case like below:
    [TestMethod]
    [DynamicData("ReusableTestDataMethod")]
    public void DynamicDataTestMethod2(int a, int b, int c)
    {
        Assert.IsTrue(1, a%3);
        Assert.IsTrue(2, b%3);
        Assert.IsTrue(0, c%3);
    }
}
```

In case, the property or method exists in different class or dll, `DynamicData` can be declared as

```
    [DynamicData(typeOf(UnitTests),"ReusableTestDataProperty")]

    [DynamicData(typeOf(UnitTests),"ReusableTestDataMethod")]

```


### Benefits of using DynamicData attribute
1. Leverages the familiar syntax of declaring inline data using `DataRow` attribute.
2. More than one tests can use the same test data, if required. 
3. Changes in the shared test data can be scoped to single place. 
