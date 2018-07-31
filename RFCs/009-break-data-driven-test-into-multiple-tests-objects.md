#Break data driven test into multiple test objects

##Summary
Allow data-driven tests to start and stop recording between each execution.

##Motivation 
When recording videos of tests using Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder data-driven tests are treated as a single block causing every execution of the test to be within the same video. See Issue [450](https://github.com/Microsoft/testfx/issues/450).

##Detailed Design

### Requirements
1. DataTestMethod Attribute should allow the option to treat it's tests as separate test objects.
2. Should not alter current behavior for existing users.

### Proposed solution
Allow a switch when using DynamicDataAttribute to allow for the optional breaking up of test videos

```csharp
[DynamicData(nameof(Data), DynamicDataSourceType.Property, separate: true )]
...
public DynamicDataAttribute(string dynamicDataSourceName, DynamicDataSourceType dynamicDataSourceType = DynamicDataSourceType.Property, bool separate = false )
{
...
}
```
