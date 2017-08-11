# RFC 007- DataSource Attribute for Data Driven Tests

## Summary
This details the MSTest V2 framework attribute "DataSource" for data driven tests where test data can be present in an excel file, xml file, sql database or OleDb.

## Motivation
At present, there are two codeflows for data-driven tests, one for DataSource Attribute and another for DataRow & DynamicData Attributes. This aims to have one codeflow for handling data-driven tests.

Also, currently DataSource Attribute does not follow framework's custom data source extensibility (i.e. `ITestDataSource`). This is because DataSource Attribute consumes test data via TestContext whereas `ITestDataSource` consumes test data in form of parameters. We will not be changing how data is consumed in dataSource Attribute purely for back compatability reasons. So, DataSource Attribute will not exactly be extended from framework's `ITestDataSource` but this is an attempt to bring the DataSource implementation closer to how it would have looked if extended from framework's data source extensibility.

## Detailed Design

### Requirements
1. DataSource and ITestDataSource should have a common code flow.
2. DataSource should provide the data for that invocation in the TestContext object.
3. Design should be extensible to support in-assembly parallelization on a data source.

### Proposed solution
The test adapter should define an interface class `ITestDataSource` (on similar lines of framework's ITestdatSource interface)which can be extended to get data from custom data source.
```csharp
    /// <summary>
    /// Interface that provides values from data source when data driven tests are run.
    /// </summary>
    public interface ITestDataSource
    {
        /// <summary>
        /// Gets the test data from custom test data source and sets dbconnection in testContext object.
        /// </summary>
        /// <param name="testMethodInfo">
        /// The info of test method.
        /// </param>
        /// <param name="testContext">
        /// Test Context object
        /// </param>
        /// <returns>
        /// Test data for calling test method.
        /// </returns>
        IEnumerable<object> GetData(UTF.ITestMethod testMethodInfo, ITestContext testContext);
    }
``` 
There is no change in how DataSource Attribute will be consumed. Test methods can be decorated as they were decorated earlier like this:
```csharp
        [TestMethod]
        [DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "MyFile.xml", "MyTable", DataAccessMethod.Sequential)]
        public void MyTestMethod()  
        {
            var v = testContext.DataRow[0];
            Assert.AreEqual(v, "3");
        }
```

The display name of tests in the above example would appear like they used to be as :
```csharp
MyTestMethod (Data Row 0)
MyTestMethod (Data Row 1)
```

### Differences between DataSource Attribute and ITestDataSource
| DataSource                                        | ITestDataSource                                        |
|---------------------------------------------------|--------------------------------------------------------|
| Test authors consume data via TestContext         | Test authors consume data via method parameters        |
| TestMethod does not require to have parameters    | TestMethod is required to have parameters              |

Note :
Test authors should not expect data to be set in TestContext for attributes inheriting from ITestDataSource. Going forward, data should only be consumed from parameters for data-driven tests. 

## Open Questions
None.  
