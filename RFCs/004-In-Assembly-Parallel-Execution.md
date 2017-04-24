# RFC 004 - In-assembly Parallel Execution

## Motivation
The key motivation is to complete the execution of a suite of tests, within a single container, faster.

Coarse-grained parallelization is already supported by vstest, and is available to all test frameworks. That works by launching test execution on each available core as a distinct process, and handing it a container worth of tests (assembly, DLL, or relevant artifact containing the tests to execute) to execute. The unit of isolation is a process. The unit of scheduling is a test container. You can read more about that in our [blogpost](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/10/parallel-test-execution/).

This document is about providing __finer-grained control__ over parallel execution __via in-assembly parallel execution of tests__ – it enables running tests within an assembly in parallel.

## Requirements:
1. Enable running tests, within an assembly, in parallel.
2. Existing tests should not break - not all existing MSTest test framework based tests might be parallel-ready.
3. To enable tests to be progressively moved to become parallel-ready, it should be possible to toggle between parallel and serial execution of tests.
4. It should be possible to indicate tests that cannot be executed in parallel.

## Approach
1. In-assembly parallel execution will be an opt-in feature.
2. Parallelization will be realized by spawning the appropriate number of threads, and handing them tests to execute.
3. There will be 3 modes of parallelization supported
    a. TestClass - each thread of execution will be handed a TestClass worth of tests to execute. Within the TestClass, the test methods will execute serially
    b. TestMethod - each thread of execution will be handed TestMethods to execute.
    c. Custom - the user will provide plugins implementing the required execution semantics. This will be covered in a separate RFC. 
4. Parallelization can be enabled with a single assembly-level attribute. This attribute will indicate the mode of parallelization using an enum parameter whose values can be as follows:

```
public enum TestParallelizationMode
{
    TestClass,
    TestMethod
}
```
5. Alternatively, it can be enabled by passing in a string parameter with the value "TestClass", "TestMethod", or a custom string (to indicate the custom parallelization mode), as shown below:
```
[assembly: TestParallelization(TestParallelizationMode)], or
[assembly: TestParallelization("TestClass")]
```
6. The number of threads spawned to execute tests can be set using a single assembly level attribute that will take a parameter whose values can be as follows:
0 - Auto configure; use as many tests as possible based on CPU and core count.
n - The number n of threads to spawn to executes tests.
```
[assembly: TestParallelizationLevel(int)];
```
7. An assembly/Class/Method can explicitly opt-out of parallelization using an attribute that will indicate that it may not be run in parallel with any other tests. The attribute does not take any arguments, and may be added at the method, class, or assembly level.
```
[DoNotParallelize()];
```
When used at the assembly level, all tests within the assembly will be executed serially.
When used at the Class level, all tests within the class will be executed serially after the parallel execution of all other tests is completed.
When used at the Method level, the test method will be executed serially after the parallel execution of all other tests is completed.
 
## Enabling parallel execution
The simplest way to enable in-assembly parallel execution is to enable it globally for all MSTest test assemblies using a .runsettings file as follows:
```
<RunSettings>
<!-- MSTest adapter -->  
  <MSTest>
    <TestParallelizationLevel>5</TestParallelizationLevel>
  </MSTest>
</RunSettings>
```
From the CLI these values can be provided using the "--" syntax.

This is as if every assembly were annotated with the following:
```
[assembly: TestParallelization(TestParallelizatonMode.TestClass)]
[assembly: TestParallelizationLevel(5)];
```
, and provides a non-intrusive way to enable in-assembly parallel execution.

Now it is quite possible that some tests will fail because they are not parallel-ready. Those test methods or test classes can then be annotated with [DoNotParallelize()]; and progressively made parallel-ready.

For finer grained control each assembly can provide annotations conditioning the mode of parallelization - this is especially required since the mode would need to account for how tests in each assembly might have been authored. In the absence of a .runsettings file, each assembly may also provide an annotation of the level of parallelization. However, the best level of parallelization that can be achieved will not differ from one assembly to another but is rather a function of the available hardware – therefore setting the level of parallelization is supported via the .runsettings file too and will take precedence.

## Notes
1. It will up to the user to ensure that the tests are parallel-ready before enabling parallel test execution.
2. Parallel execution will have an impact on data collectors. Since test execution will be in parallel, the start/end events marking the execution of a particular test might get interleaved with those of any other test that might be executing in parallel. It will be up to the data collectors to be resilient.
3. Diagnosing test failures during parallel execution will require appropriately formatted logging. The adapter should take care to straighten out the logs and emit them appropriately formatted.
