# RFC 009- Deployment Item Attribute for Net Core

## Summary
This details the MSTest V2 framework attribute `DeploymentItem` for copying files or folders specified as deployment items to the deployment directory. Deployment directory is where all the deployment items are present along with TestSource dll.

## Motivation
Many a times, a test author takes dependency on certain files(like .dll, .xml, .txt etc.) and requires those files to be present in test run location at the time of test execution. Instead of manually copying the files, he/she can leverage the 'DeploymentItem' attribute provided by MSTest adapter to deploy those files to the test run location/deployment directory.

## Features
1. It can be used either on TestClass or on TestMethod.
2. User can specify a directory in which case it'll deploy all the files of that directory recursively.
3. User can specify their own output paths inside the deployment directory using the second argument of DeploymentItem.
4. Path of deployment item can be either be absolute or relative to the deployment directory.
5. Can have multiple instances of the attribute to specify more than one item.

## Example
```csharp
    [TestClass]
    [DeploymentItem(@"C:\classLevelDepItem.xml")]   //absolute path
    public class UnitTest1
    {
        [TestMethod]
        [DeploymentItem(@"..\..\methodLevelDepItem1.xml")]   //relative path
        [DeploymentItem(@"C:\DataFiles\methodLevelDepItem2.xml", "DataFiles")]   //custom output path
        public void TestMethod1()
        {
            String textFromFile = File.ReadAllText("classLevelDepItem.xml");
        }
    }
```

## Behavior Changes wrt FullFramework
1. In FullFramework, tests run from a newly created deployment directory ProjectRoot\TestResults\Deploy_*username* *timestamp*\Out. In NetCore, tests run from ProjectRoot\ProjectRoot\bin\Debug\netcoreapp2.1 directory.      
2. Dependencies of DeploymentItem are by default deployed in FullFramework. Users can override this by specifying `DeployTestSourceDependencies` as false in RunSettings. Since dependencies of deployment items are not deployed in NetCore, `DeployTestSourceDependencies` setting will not be honored.

## Limitations
1. Error messages are supported only in English language yet. It'll be fixed as part of https://github.com/Microsoft/testfx/issues/591.
