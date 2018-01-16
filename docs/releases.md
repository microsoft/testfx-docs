# Release Notes

## 1.3.0-beta2
Fixes part of this release:
 1. In-Assembly Parallel Feature. [#296](https://github.com/Microsoft/testfx/pull/296)
 2. Add missing Microsoft.Internal.TestPlatform.ObjectModel [#301](https://github.com/Microsoft/testfx/pull/301) [Contributed by [Andrey Kurdyumov](https://github.com/kant2002)]
 3. Adding warning message for vsmdi file [#61](https://github.com/Microsoft/testfx/issues/61)
 4. Fixing Key collision for test run parameters [#298](https://github.com/Microsoft/testfx/issues/298)
 5. Fix for csv x64 scenario [#325](https://github.com/Microsoft/testfx/issues/325)
 6. DataRow DisplayName Fix in .Net framework [#284](https://github.com/Microsoft/testfx/issues/284)
 7. Update File version for adapter and framework dlls [#268](https://github.com/Microsoft/testfx/issues/268)
 8. Add information about which assembly failed to discover test [#299](https://github.com/Microsoft/testfx/pull/299) [Contributed by [Andrey Kurdyumov](https://github.com/kant2002)]
 
 A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.2.0...v1.3.0-beta2)

### Builds
 
* MSTest.TestFramework: [1.3.0-beta2](https://www.nuget.org/packages/MSTest.TestFramework/1.3.0-beta2)
* MSTest.TestAdapter: [1.3.0-beta2](https://www.nuget.org/packages/MSTest.TestAdapter/1.3.0-beta2)

## 1.2.0
Fixes part of this release:
 1. DataSourceAttribute Implementation (#238)
 2. Adding support for DiaNavigation in UWP test adapter (#258)
 3. Wrong order of arguments to ArgumentException (#262)
 4. Adding filtering support at discovery (#271)
 5. Improve handling of Assert.Inconclusive (#277)
 
 A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.2.0-beta3...v1.2.0)

### Builds
 
* MSTest.TestFramework: [1.2.0](https://www.nuget.org/packages/MSTest.TestFramework/1.2.0)
* MSTest.TestAdapter: [1.2.0](https://www.nuget.org/packages/MSTest.TestAdapter/1.2.0)

## 1.2.0-beta3
Fixes part of this release:
 1. Added Mapping for TestOutcome.None to the UnitTestOutcome Enum to achieve NotExecuted behaviour in VSTS. [#217](https://github.com/Microsoft/testfx/issues/217) [Contributed By [Irguzhav](https://github.com/irguzhav)] [enhancement]
 2. TestMethod failures masked by TestCleanUp exceptions. [#58](https://github.com/Microsoft/testfx/issues/58)
 3. Multiple copies added for same test on running multiple times in IntelliTest. [#92](https://github.com/Microsoft/testfx/issues/92)
 4. Adapter is not sending TestCategory traits in Testcase object to Testhost. [#189](https://github.com/Microsoft/testfx/issues/189) 
 5. All the Assert constructor's has been made private and the classes sealed. [#223](https://github.com/Microsoft/testfx/issues/223)
 
 A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.2.0-beta...v1.2.0-beta3)
 
 ### Builds
 
* MSTest.TestFramework: [1.2.0-beta3](https://www.nuget.org/packages/MSTest.TestFramework/1.2.0-beta3)
* MSTest.TestAdapter: [1.2.0-beta3](https://www.nuget.org/packages/MSTest.TestAdapter/1.2.0-beta3)

## 1.2.0-beta
Fixes part of this release:
 1. Support for Dynamic Data Attribute. [#141](https://github.com/Microsoft/testfx/issues/141) [extensibility]
 2. Make discovering test methods from base classes defined in another assembly the default. [#164](https://github.com/Microsoft/testfx/issues/164) [enhancement]
 3. CollectSourceInformation awareness to query source information . [#119](https://github.com/Microsoft/testfx/issues/119) [enhancement]
 
 A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.1.18...v1.2.0-beta)
 
 ### Builds
 
* MSTest.TestFramework: [1.2.0-beta](https://www.nuget.org/packages/MSTest.TestFramework/1.2.0-beta)
* MSTest.TestAdapter: [1.2.0-beta](https://www.nuget.org/packages/MSTest.TestAdapter/1.2.0-beta)

## 1.1.18
Fixes part of this release:
 1. Ability to provide a reason for Ignored tests. [#126](https://github.com/Microsoft/testfx/issues/126) [enhancement]
 2. VB unit test project templates that ship in VS 2017 do not reference MSTest V2 nuget packages. [#132](https://github.com/Microsoft/testfx/issues/132) [enhancement]
 3. Assert.IsInstanceOf passes on value null. [#178](https://github.com/Microsoft/testfx/issues/178) [Contributed By [LarsCelie](https://github.com/larscelie)]
 4. Test methods in a base class defined in a different assembly are not navigable in Test Explorer. [#163](https://github.com/Microsoft/testfx/issues/163) [Contributed By [ajryan](https://github.com/ajryan)]
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
