<p align="center">
  <img src="https://travis-ci.org/bagdemir/rhino.svg?branch=master"/>
  <img src="https://img.shields.io/badge/rhino%20sdk-1.1.11-green.svg"/>
  <img src="https://img.shields.io/badge/archetype-1.1.11-blue.svg" />
</p>


## Rhino: Load and Performance Testing

Rhino is a lightweight annotation-based JUnit-style load and performance testing framework tailored 
for 
testing web services which consists of the Rhino Java framework as well as a collection of libraries
 and tools which enable developers to develop load and performance tests very fast. The Rhino can be 
 added as library dependency into your project.

**Rhino's philosophy is basically:**

* to speed up load and performance tCIest development,
* a debuggable test framework written in Java, so that you can go through the breakpoints while 
investigating problems in your load testing code, 
* to enable the integration with the existing code, e.g your integration test frameworks to 
make them reusable in your load and performance test,
* to provide an intuitive framework so that the engineers do not need to re-learn the language, or
the framework every time they need to write new load tests.

Considering all these aspects, we began with Project Rhino in 2018 and it is available as OSS  
with Apache 2.0 License, now.

## How do the load tests look like?

Simulation is a test entity which will be executed and generates load according to the 
implementation provided in the test classes against the instance under test, e.g a web 
service. So as to create a new simulation entity, create a plain Java object with `@Simulation` 
annotation: 

```java
@Simulation(name = "Example Simulation")
public class PerformanceTestingExample {
}
```

The simulation above does nothing unless we add some scenarios to it. A scenario is a method 
annotated with `@Scenario` annotation and contains the implementation of the load generation. A simulation 
might have multiple scenarios defined which are run during testing, independently and parallel:

```java
@Simulation(name = "Example Simulation")
public class PerformanceTestingExample {
  
  @Feeder
  private User myAuthUser;

  @Scenario(name = "Hello World")
  public void testHelloWorld(Recorder recorder) {
    // hello world
  }

  @Scenario(name = "Health Check")
  public void testHealthCheck(Recorder recorder) {
    // healthcheck 
  }
}
```

The name of the simulation is important. In a performance testing project, it is very likely that 
you will have multiple simulations. Rhino does know which simulation is to be run from the 
simulation name provided, so the names must be unique. 

## Get Started

If you think that the Rhino is the right framework for you, you can follow the wiki to get started:

* [Getting started with Rhino load testing](https://github.com/bagdemir/rhino/wiki/Getting-Started)
* [Simulations](https://github.com/bagdemir/rhino/wiki/Simulations)

Questions/Contributions?
---

Feel free to fork the project and make contributions in terms of Pull Requests. For bigger 
proposals, architectural discussions and bug reports, use the Github's issue tracker.
