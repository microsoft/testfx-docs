# RFC 005- DynamicData Attribute for Data Driven Tests

## Summary
This details the MSTest V2 framework attribute "DynamicData" for data driven tests where data can be specified as property.

## Motivation
Often times, the inline test data need to be shared between tests. There could be more than one test cases in different files which will we using same test data. In most of these situations, user end up declaring same inline data for multiple test cases using "DataRow" attribute. Test framework should provides an attribute so that test data, declared as property, can be
* Easily re-used
* Easily organized

## Detailed Design

### Requirements
1. Test data declared as property should be easily asscoaited with test case.
2. Test data declared as property should be associated with more than one test cases, if required.

### Proposed solution
Here is a solution that meets the above requirements:

The property storing test data should be declared as static.
```
    static object[] ReusableTestData =
        {
            new object[] {1, 2, 3},
            new object[] {4, 5, 6}
        };
```

This property can then be used to associate test data with data driven test case like below:
```
    [TestMethod]
    [DynamicData("ReusableTestData")]
    public void DynamicDataTestMethod(int a, int b, int c)
    {
        Assert.IsTrue(1, a%3);
        Assert.IsTrue(2, b%3);
        Assert.IsTrue(3, c%3);
    }
```
In a similary way, same test data can be associated with multiple test cases.

### Benefits of using DynamicData attribute
1. Leverages the familiar syntax of declaring inline data using DataRow attribute.
2. More than one tests can use the same test data, if required. 
3. Changes in the data can be scoped to single place for scenarios where test data is shared. 

## Open questions
1. Should we support methods and fields as well?



