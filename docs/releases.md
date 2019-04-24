# Releases

# 2.0.0-beta4 (April 2019)
 - [x] [Deployment Item support in .NET Core](https://github.com/Microsoft/testfx/pull/565) 
 - [x] [Support for CancellationTokenSource in TestContext to help in timeout scenario](https://github.com/Microsoft/testfx/pull/585)
 - [x] [Correcting error message when DynamicData doesn't have any data](https://github.com/Microsoft/testfx/issues/443)

A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/2.0.0-beta2...v2.0.0-beta4) 

### Builds
* MSTest.TestFramework: [2.0.0-beta4](https://www.nuget.org/packages/MSTest.TestFramework/2.0.0-beta4)
* MSTest.TestAdapter: [2.0.0-beta4](https://www.nuget.org/packages/MSTest.TestAdapter/2.0.0-beta4)

 # 2.0.0-beta2 (February 2019)
 - [x] (BREAKING CHANGE) [TestContext Properties type fixed to be IDictionary](https://github.com/Microsoft/testfx/pull/563) 
 - [x] [Base class data rows should not be executed](https://github.com/Microsoft/testfx/pull/546)
 - [x] [Setting option for marking not runnable tests as failed](https://github.com/Microsoft/testfx/pull/524)

A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/1.4.0...2.0.0-beta2) 

### Builds
* MSTest.TestFramework: [2.0.0-beta2](https://www.nuget.org/packages/MSTest.TestFramework/2.0.0-beta2)
* MSTest.TestAdapter: [2.0.0-beta2](https://www.nuget.org/packages/MSTest.TestAdapter/2.0.0-beta2)

# 1.4.0 (November 2018)
 - [x] (BREAKING CHANGE) [Description, WorkItem, CssIteration, CssProjectStructure Attributes will not be treated as traits](https://github.com/Microsoft/testfx/pull/482) 
 - [x] [Added new runsettings configuration to deploy all files from test source location i.e. DeployTestSourceDependencies](https://github.com/Microsoft/testfx/pull/391) [enhancement]
 - [x] [Removed Test discovery warnings in Test Output pane](https://github.com/Microsoft/testfx/pull/480) [Contributed by [Carlos Parra](https://github.com/parrainc)]
 - [x] [Allow test methods returning Task to run without suppling async keyword](https://github.com/Microsoft/testfx/pull/510) [Contributed by [Paul Spangler](https://github.com/spanglerco)]

A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/1.4.0-beta...1.4.0) 

### Builds
* MSTest.TestFramework: [1.4.0](https://www.nuget.org/packages/MSTest.TestFramework/1.4.0)
* MSTest.TestAdapter: [1.4.0](https://www.nuget.org/packages/MSTest.TestAdapter/1.4.0)

# 1.4.0-beta (October 2018)
 - [x] [Enabling Tfs properties in test context object](https://github.com/Microsoft/testfx/pull/472) [enhancement]
 - [x] [Description, WorkItem, CssIteration, CssProjectStructure Attributes should not be treated as traits](https://github.com/Microsoft/testfx/pull/482) 
 - [x] [Adding appropriate error message for TestMethods expecting parameters but parameters not provided](https://github.com/Microsoft/testfx/pull/457)

A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/1.3.2...1.4.0-beta) 

### Builds
* MSTest.TestFramework: [1.4.0-beta](https://www.nuget.org/packages/MSTest.TestFramework/1.4.0-beta)
* MSTest.TestAdapter: [1.4.0-beta](https://www.nuget.org/packages/MSTest.TestAdapter/1.4.0-beta)
 
# 1.3.2 (June 2018)
 - [x] [Hierarchical view support for data-driven tests ](https://github.com/Microsoft/testfx/pull/417)

A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.3.1...v1.3.2)
 
### Builds
* MSTest.TestFramework: [1.3.2](https://www.nuget.org/packages/MSTest.TestFramework/1.3.2)
* MSTest.TestAdapter: [1.3.2](https://www.nuget.org/packages/MSTest.TestAdapter/1.3.2)
 
# 1.3.1 (May 2018)
 - [x] [AppDomain creation should honor runsettings ](https://github.com/Microsoft/testfx/pull/427)
 - [x] [Don't delete resource folder while clean/rebuild ](https://github.com/Microsoft/testfx/pull/424) 

 A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.3.0...v1.3.1)
 
### Builds
* MSTest.TestFramework: [1.3.1](https://www.nuget.org/packages/MSTest.TestFramework/1.3.1)
* MSTest.TestAdapter: [1.3.1](https://www.nuget.org/packages/MSTest.TestAdapter/1.3.1)

# 1.3.0 (May 2018)
 - [x] [TestTimeout configurable via RunSettings](https://github.com/Microsoft/testfx/pull/403) [enhancement] 
 - [x] [Customize display name for DynamicDataAttribute](https://github.com/Microsoft/testfx/pull/373) [Contributed by [Brad Stoney](https://github.com/bstoney)] [enhancement]
 - [x] [Fix incompatibility between multiple versions of mstest adapter present in a solution](https://github.com/Microsoft/testfx/pull/404)
 - [x] [Fix multiple results not returning for custom TestMethod](https://github.com/Microsoft/testfx/pull/363) [Contributed by [Cédric Bignon](https://github.com/bignoncedric)]
 - [x] [Run Class Cleanup in sync with Class Initialize](https://github.com/Microsoft/testfx/pull/372)
 - [x] [Fix to show right error message on assembly load exception during test run](https://github.com/Microsoft/testfx/issues/395)
 - [x] [Consistent behavior of GenericParameterHelper's while running and debugging](https://github.com/Microsoft/testfx/issues/362) [Contributed by [walterlv](https://github.com/walterlv)]
 
A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.2.1...v1.3.0)

### Builds
* MSTest.TestFramework: [1.3.0](https://www.nuget.org/packages/MSTest.TestFramework/1.3.0)
* MSTest.TestAdapter: [1.3.0](https://www.nuget.org/packages/MSTest.TestAdapter/1.3.0)

# 1.3.0-beta2 (January 2018)
 - [x] [In-Assembly Parallel Feature](https://github.com/Microsoft/testfx/pull/296)
 - [x] [Add missing Microsoft.Internal.TestPlatform.ObjectModel](https://github.com/Microsoft/testfx/pull/301) [Contributed by [Andrey Kurdyumov](https://github.com/kant2002)]
 - [x] [Adding warning message for vsmdi file](https://github.com/Microsoft/testfx/issues/61)
 - [x] [Fixing Key collision for test run parameters](https://github.com/Microsoft/testfx/issues/298)
 - [x] [Fix for csv x64 scenario](https://github.com/Microsoft/testfx/issues/325)
 - [x] [DataRow DisplayName Fix in .Net framework](https://github.com/Microsoft/testfx/issues/284)
 - [x] [Update File version for adapter and framework dlls](https://github.com/Microsoft/testfx/issues/268)
 - [x] [Add information about which assembly failed to discover test](https://github.com/Microsoft/testfx/pull/299) [Contributed by [Andrey Kurdyumov](https://github.com/kant2002)]
 
A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.2.0...v1.3.0-beta2)

### Builds
* MSTest.TestFramework: [1.3.0-beta2](https://www.nuget.org/packages/MSTest.TestFramework/1.3.0-beta2)
* MSTest.TestAdapter: [1.3.0-beta2](https://www.nuget.org/packages/MSTest.TestAdapter/1.3.0-beta2)

# 1.2.1 (April 2018)
 - [x] [Fixing Key collision for test run parameters](https://github.com/Microsoft/testfx/pull/328)
 - [x] [Don't call Class Cleanup if Class Init not called](https://github.com/Microsoft/testfx/pull/372)
 - [x] [Fix masking assembly load failure error message](https://github.com/Microsoft/testfx/pull/382)
 - [x] [Fix UWP tests discovery](https://github.com/Microsoft/testfx/pull/332)
 
### Builds
* MSTest.TestFramework: [1.2.1](https://www.nuget.org/packages/MSTest.TestFramework/1.2.1)
* MSTest.TestAdapter: [1.2.1](https://www.nuget.org/packages/MSTest.TestAdapter/1.2.1)

# 1.2.0 (October 2017)
 - [x] [DataSourceAttribute Implementation](https://github.com/Microsoft/testfx/pull/238)
 - [x] [Adding support for DiaNavigation in UWP test adapter](https://github.com/Microsoft/testfx/pull/258)
 - [x] [Arguments order for ArgumentException](https://github.com/Microsoft/testfx/pull/262)
 - [x] [Adding filtering support at discovery](https://github.com/Microsoft/testfx/pull/271)
 - [x] [Improve handling of Assert.Inconclusive](https://github.com/Microsoft/testfx/pull/277)
 
A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.2.0-beta3...v1.2.0)

### Builds
* MSTest.TestFramework: [1.2.0](https://www.nuget.org/packages/MSTest.TestFramework/1.2.0)
* MSTest.TestAdapter: [1.2.0](https://www.nuget.org/packages/MSTest.TestAdapter/1.2.0)

# 1.2.0-beta3 (August 2017)
 - [x] [Added Mapping for TestOutcome.None to the UnitTestOutcome Enum to achieve NotExecuted behaviour in VSTS](https://github.com/Microsoft/testfx/issues/217) [Contributed By [Irguzhav](https://github.com/irguzhav)] [enhancement]
 - [x] [TestMethod failures masked by TestCleanUp exceptions](https://github.com/Microsoft/testfx/issues/58)
 - [x] [Multiple copies added for same test on running multiple times in IntelliTest](https://github.com/Microsoft/testfx/issues/92)
 - [x] [Adapter is not sending TestCategory traits in Testcase object to Testhost](https://github.com/Microsoft/testfx/issues/189) 
 - [x] [All the Assert constructor's has been made private and the classes sealed](https://github.com/Microsoft/testfx/issues/223)
 
A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.2.0-beta...v1.2.0-beta3)
 
### Builds
* MSTest.TestFramework: [1.2.0-beta3](https://www.nuget.org/packages/MSTest.TestFramework/1.2.0-beta3)
* MSTest.TestAdapter: [1.2.0-beta3](https://www.nuget.org/packages/MSTest.TestAdapter/1.2.0-beta3)

# 1.2.0-beta (June 2017)
 - [x] [Support for Dynamic Data Attribute](https://github.com/Microsoft/testfx/issues/141) [extensibility]
 - [x] [Make discovering test methods from base classes defined in another assembly the default](https://github.com/Microsoft/testfx/issues/164) [enhancement]
 - [x] [CollectSourceInformation awareness to query source information](https://github.com/Microsoft/testfx/issues/119) [enhancement]
 
A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.1.18...v1.2.0-beta)
 
### Builds
* MSTest.TestFramework: [1.2.0-beta](https://www.nuget.org/packages/MSTest.TestFramework/1.2.0-beta)
* MSTest.TestAdapter: [1.2.0-beta](https://www.nuget.org/packages/MSTest.TestAdapter/1.2.0-beta)

# 1.1.18 (June 2017)
 - [x] [Ability to provide a reason for Ignored tests](https://github.com/Microsoft/testfx/issues/126) [enhancement]
 - [x] [VB unit test project templates that ship in VS 2017 do not reference MSTest V2 nuget packages](https://github.com/Microsoft/testfx/issues/132) [enhancement]
 - [x] [Assert.IsInstanceOf passes on value null](https://github.com/Microsoft/testfx/issues/178) [Contributed By [LarsCelie](https://github.com/larscelie)]
 - [x] [Test methods in a base class defined in a different assembly are not navigable in Test Explorer](https://github.com/Microsoft/testfx/issues/163) [Contributed By [ajryan](https://github.com/ajryan)]
 - [x] [Enable MSTest framework based tests targeting .NET Core to be run and debugged from within VSCode](https://github.com/Microsoft/testfx/issues/182)
 - [x] [Web project templates that ship in VS 2017 do not reference MSTest V2 nuget packages](https://github.com/Microsoft/testfx/issues/167) 
 
A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.1.17...v1.1.18)
 
### Builds
* MSTest.TestFramework: [1.1.18](https://www.nuget.org/packages/MSTest.TestFramework/1.1.18)
* MSTest.TestAdapter: [1.1.18](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.18)

# 1.1.17 (April 2017)
 - [x] [Console.WriteLine support for .NetCore Projects](https://github.com/Microsoft/testfx/issues/18) [enhancement]
 - [x] [Inheritance support for base classes that resides in different assemblies](https://github.com/Microsoft/testfx/issues/23) [enhancement]
 - [x] [TestContext.Writeline does not output messages](https://github.com/Microsoft/testfx/issues/120)
 - [x] [Logger.LogMessage logs a message mutliple times](https://github.com/Microsoft/testfx/issues/114)
 - [x] [TestContext.CurrentTestOutcome is always InProgress in the TestCleanup method](https://github.com/Microsoft/testfx/issues/89)
 - [x] [An inconclusive in a test initialize fails the test if it has an ExpectedException](https://github.com/Microsoft/testfx/issues/136) 
 
A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.1.14...v1.1.17)
 
### Builds
* MSTest.TestFramework: [1.1.17](https://www.nuget.org/packages/MSTest.TestFramework/1.1.17)
* MSTest.TestAdapter: [1.1.17](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.17)

# 1.1.14 (March 2017)
 - [x] [Ability to add custom assertions](https://github.com/Microsoft/testfx/issues/116) [enhancement]
 - [x] [Problems with null in DataRow](https://github.com/Microsoft/testfx/issues/70)
 
A list of changes since last release are available [here](https://github.com/Microsoft/testfx/compare/v1.1.13...v1.1.14)
 
### Builds
* MSTest.TestFramework: [1.1.14](https://www.nuget.org/packages/MSTest.TestFramework/1.1.14)
* MSTest.TestAdapter: [1.1.14](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.14)

# 1.1.13 (March 2017)
 - [x] [Tests with Deployment Item do not run](https://github.com/Microsoft/testfx/issues/91)
 - [x] [Run tests fail intermittently with a disconnected from server exception](https://github.com/Microsoft/testfx/issues/28)
 - [x] [Templates and Wizards vsix should be built with RC3 tooling](https://github.com/Microsoft/testfx/issues/77)

This is also the first release from GitHub and with source code building against Dev15 tooling.

### Builds
* MSTest.TestFramework: [1.1.13](https://www.nuget.org/packages/MSTest.TestFramework/1.1.13)
* MSTest.TestAdapter: [1.1.13](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.13)

# 1.1.11 (February 2017)
Initial release.
### Builds
* MSTest.TestFramework: [1.1.11](https://www.nuget.org/packages/MSTest.TestFramework/1.1.11)
* MSTest.TestAdapter: [1.1.11](https://www.nuget.org/packages/MSTest.TestAdapter/1.1.11)
