## Behaviour changes w.r.t MSTest V1
 
Listed are the difference in behaviour of MSTest V2 w.r.t MSTest V1 :
1. Test methods from base classes defined in another assembly are now discovered and run from the derived Test class. This brings in a consistent behavior with derived test class types. If this behavior is not required for compat reasons it can be changed back using the following runsettings:
 ```
 <RunSettings>    
  <MSTest> 
    <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
  </MSTest> 
</RunSettings>
```
2. The TestCleanup method on a TestClass is invoked even if its corresponding TestInitialize method fails. See [#250](https://github.com/Microsoft/testfx/issues/250) for details.
