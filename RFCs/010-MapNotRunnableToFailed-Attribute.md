# RFC 010 - Map not runnable tests to failed via runsettings

## Motivation
Some tests which have incompatible signature and cannot be executed are skipped with warnings being thrown.
User should be able to configure to fail a test if it is not runnable. 

### Proposed solution
Make this setting configurable via MapNotRunnableToFailed tag which is part of the adapter node in the runsettings.

Here is a sample runsettings: 
```xml
<Runsettings> 
  <MSTestV2> 
    <MapNotRunnableToFailed>true</MapNotRunnableToFailed>   
  </MSTestV2> 
</Runsettings> 
```

### Honoring the settings 
- If no settings are provided in runsettings, default MapNotRunnableToFailed is set to true. 
  This has been kept to fail the tests which cannot be executed and avoid silent failures.
- The setting can be overridden by specifying `MapNotRunnableToFailed>false</MapNotRunnableToFailed>` in the adapter settings.
