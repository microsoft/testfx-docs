# Release Notes

## 1.1.18
Fixes part of this release:
 1. Ability to provide a reason for Ignored tests. [#126](https://github.com/Microsoft/testfx/issues/126) [enhancement]
 2. VB unit test project templates that ship in VS 2017 do not reference MSTest V2 nuget packages. [#132](https://github.com/Microsoft/testfx/issues/132) [enhancement]
 3. Assert.IsInstanceOf passes on value null. [#178](https://github.com/Microsoft/testfx/issues/178) [Contributed By @LarsCelie(https://github.com/larscelie)]
 4. Test methods in a base class defined in a different assembly are not navigable in Test Explorer. [#163](https://github.com/Microsoft/testfx/issues/163) [Contributed By @ajryan(https://github.com/ajryan)]
 5. Enable MSTest framework based tests targeting .NET Core to be run and debugged from within VSCode. [#182](https://github.com/Microsoft/testfx/issues/182)
 6. Web project templates that ship in VS 2017 do not reference MSTest V2 nuget packages. [#167](https://github.com/Microsoft/testfx/issues/167) 
 
 A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.1.17...v1.1.18)
 
 ### Builds
 
* MSTest.TestFramework: [1.1.18](https://www.nuget.org/packages/MSTest.TestFramework/1.1.18)
* MSTest.TestAdapter: [1.1.18](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.18)

## 1.1.17
Fixes part of this release:
 1. Console.WriteLine support for .NetCore Projects . [#18](https://github.com/Microsoft/testfx/issues/18) [enhancement]
 2. Inheritance support for base classes that resides in different assemblies. [#23](https://github.com/Microsoft/testfx/issues/23) [enhancement]
 3. TestContext.Writeline does not output messages. [#120](https://github.com/Microsoft/testfx/issues/120)
 4. Logger.LogMessage logs a message mutliple times. [#114](https://github.com/Microsoft/testfx/issues/114)
 5. TestContext.CurrentTestOutcome is always InProgress in the TestCleanup method. [#89](https://github.com/Microsoft/testfx/issues/89)
 6. An inconclusive in a test initialize fails the test if it has an ExpectedException. [#136](https://github.com/Microsoft/testfx/issues/136) 
 
 A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.1.14...v1.1.17)
 
 ### Builds
 
* MSTest.TestFramework: [1.1.17](https://www.nuget.org/packages/MSTest.TestFramework/1.1.17)
* MSTest.TestAdapter: [1.1.17](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.17)

## 1.1.14
Fixes part of this release:
 1. Ability to add custom assertions. [#116](https://github.com/Microsoft/testfx/issues/116) [enhancement]
 2. Problems with null in DataRow. [#70](https://github.com/Microsoft/testfx/issues/70)
 
 A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.1.13...v1.1.14)
 
 ### Builds
 
* MSTest.TestFramework: [1.1.14](https://www.nuget.org/packages/MSTest.TestFramework/1.1.14)
* MSTest.TestAdapter: [1.1.14](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.14)

## 1.1.13
Fixes part of this release:
 1. Tests with Deployment Item do not run. [#91](https://github.com/Microsoft/testfx/issues/91)
 2. Run tests fail intermittently with a disconnected from server exception. [#28](https://github.com/Microsoft/testfx/issues/28)
 3. Templates and Wizards vsix should be built with RC3 tooling [#77](https://github.com/Microsoft/testfx/issues/77)

This is also the first release from GitHub and with source code building against Dev15 tooling.

### Builds

* MSTest.TestFramework: [1.1.13](https://www.nuget.org/packages/MSTest.TestFramework/1.1.13)
* MSTest.TestAdapter: [1.1.13](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.13)
