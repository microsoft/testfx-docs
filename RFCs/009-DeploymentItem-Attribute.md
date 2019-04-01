# RFC 009- Deployment Item Attribute for Net Core

## Summary
This details the MSTest V2 framework attribute `DeploymentItem` for copying files or folders specified as deployment items to the deployment directory. Deployment directory is where all the deployment items are present along with source dll.

## Motivation
Often, user might need certain files (.dll, .xml, .txt etc.) during test execution. Users can use `DeploymentItem` for declaring such files.

## Features
1. It can be used either on TestClass or on TestMethod.
2. User can specify a directory in which case it'll deploy all the files of that directory recursively.
3. User can specify their own output paths inside the deployment directory using the second argument of DeploymentItem.
4. Path of deployment item can be either be absolute or relative to the deployment directory.
5. Can have multiple instances of the attribute to specify more than one item.

## Example
```csharp
    [TestClass]
    [DeploymentItem(@"C:\classLevelDepItem.xml")]
    public class UnitTest1
    {
        [TestMethod]
        [DeploymentItem(@"..\..\methodLevelDepItem1.xml")]
        [DeploymentItem(@"C:\DataFiles\methodLevelDepItem2.xml", "DataFiles")]
        public void TestMethod1()
        {
            String textFromFile = File.ReadAllText("classLevelDepItem.xml");
        }
    }
```

## Differences with DeploymentItem of FullFramework
1. In FullFramework, tests run from a newly created deployment directory ProjectRoot\TestResults\Deploy_*username* *timestamp*\Out. In NetCore, tests run from ProjectRoot\ProjectRoot\bin\Debug\netcoreapp2.1 directory.      
2. Dependencies of DeploymentItem are also deployed in FullFramework but not in NetCore.

## Limitations
1. Error messages are supported only in English language yet.
2. Since dependencies of deployment items are not deployed, DeployTestSourceDependencies of RunSettings will not be honored.
