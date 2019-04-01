# RFC 009- Deployment Item Attribute

## Summary
This details the MSTest V2 framework attribute `DeploymentItem` for copying files or folders specified as deployment items to the deployment directory.

## Motivation
Often times, user might need a certain files(.dll, .xml, .txt etc.) during test execution. Users can use `DeploymentItem` for declaring such files.

## Features
1. It can be used either on TestClass or on TestMethod.
2. User can specify a directory in which case it'll deploy all the files of that directory recursively.
3. User can specify their own output paths inside the deployment directory using the second argument of DeploymentItem.
4. User can either give paths of deployment items as either absolute or relative to the deployment directory.
5. Can have multiple instances of the attribute to specify more than one item.

```csharp
[DeploymentItem(@"C:\temp\FileToDeploy.xml")]

[DeploymentItem(@"C:\temp")]

[DeploymentItem(@"C:\temp\FileToDeploy.xml", "DataFiles")]
```

## Differences in how DeploymentItem works in FullFramework and NetCore
1. In FullFramework, a new deployment directory is created where all the items required for test execution are copied and tests are run from that directory. This directory is deleted after test execution is complete. However in NetCore, tests are run from the debug directory and hence DeploymentItems are copied to debug directory. This directory is not deleted after test execution is complete.
2. If the DeploymentItem is an executable, its dependencies are also deployed in FullFramework but not in NetCore.
