As part of the Spring Boot upgrade you may want to upgrade or migrate from JUnit 4 to JUnit 5. There are benefits to making this change, but if you have a large test suite you may be better served planning this work separately, and decoupling it from the Spring Boot Upgrade.

## Why Would You Want To Move to JUnit 5?

JUnit 5 is an attempt by the library/framework developers to address some shortcomings of JUnit 4. Specifically:

- JUnit 4 was packaged as a single jar library requiring you to import the entire library, even if you only want to use a single feature. JUnit 5 allows you to make discrete imports from the library.
- JUnit 4 would only allow a single test runner to execute tests at a time. JUnit 5 supports concurrent test runners.
- JUnit 4 was built and designed around the features of Java 7. JUnit 5 has been updated and uses features of Java 8.

## What Are Some Key Changes?

**Annotations:**

- `@Before` annotation is now `@BeforeEach`
- `@After` annotation is now `@AfterEach`
- `@BeforeClass` annotation is now `@BeforeAll`
- `@AfterClass` annotation is now `@AfterAll`
- `@RunWith` annotation is now `@Extendwith`

### JUnit 5 Vintage

This library allows for running JUnit 3 and JUnit4 tests within the JUnit 5 Context and provides a path for an ordered migration in lieu of mass migration.

From the [documentation](https://junit.org/junit5/docs/current/user-guide/#migrating-from-junit4):

> JUnit provides a gentle migration path via a _JUnit Vintage test engine_ which allows existing tests based on JUnit 3 and JUnit 4 to be executed using the JUnit Platform infrastructure.

Explore this migration option if it's better for your application.
