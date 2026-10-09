Ok, lets look at the skipped test.

1.  Find the skipped test(s).

    Search for `@Disabled` in the Editor and find the `skipped` test.

    ```editor:select-matching-text
    file: ~/exercises/src/test/java/example/cashcard/CashCardApplicationTests.java
    text: "@Disabled"
    ```

    This `skipped` test should look like this:

    ```java
    @Disabled
    void shouldReturnACashCardWhenDataIsSaved() {
        ResponseEntity<String> response = restTemplate
                .withBasicAuth("sarah1", "abc123")
                .getForEntity("/cashcards/99", String.class);
        assertThat(response.getStatusCode()).isEqualTo(HttpStatus.OK);

        DocumentContext documentContext = JsonPath.parse(response.getBody());
        Number id = documentContext.read("$.id");
        assertThat(id).isEqualTo(99);

        Double amount = documentContext.read("$.amount");

        // Lesson 1.2 - This should test for 123.45
        assertThat(amount).isEqualTo(12.45);
    }
    ```

2.  Enable the test and rerun.

    Comment out the `@Disabled` annotation to enable the test.

    ```java
    // @Disabled
    void shouldReturnACashCardWhenDataIsSaved() {
    ...
    }
    ```

    Rerun the test. Does it pass?

    **_Note:_** we're passing in `-Dtest` to specify the one test we want to run.

    Open the **Terminal** and run the tests:

    ```dashboard:open-dashboard
    name: Terminal
    ```

    ```shell
    [~/exercises] $ ./mvnw  test -Dtest=CashCardApplicationTests#shouldReturnACashCardWhenDataIsSaved
    ```

    Output should look similar to the following:

    ```shell
    [ERROR] Tests run: 1, Failures: 1, Errors: 0, Skipped: 0, Time elapsed: 10.096 s <<< FAILURE! - in example.cashcard.CashCardApplicationTests
    [ERROR] shouldReturnACashCardWhenDataIsSaved  Time elapsed: 1.746 s  <<< FAILURE!
    org.opentest4j.AssertionFailedError:

    expected: 12.45
        but was: 123.45
            at example.cashcard.CashCardApplicationTests.shouldReturnACashCardWhenDataIsSaved(CashCardApplicationTests.java:43)

    [INFO]
    [INFO] Results:
    [INFO]
    [ERROR] Failures:
    [ERROR]   CashCardApplicationTests.shouldReturnACashCardWhenDataIsSaved:43
    expected: 12.45
        but was: 123.45
    [INFO]
    [ERROR] Tests run: 1, Failures: 1, Errors: 0, Skipped: 0
    [INFO]
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD FAILURE
    [INFO] ------------------------------------------------------------------------
    ```

    We can see that an assertion failed. Let's fix it.

3.  Fix the test.

    We can see that an assertion failed.

    A bit of investigation will reveal that the correct expected value is `123.45`.

    This is a simple enough change, so let's fix the expectation:

    ```java
    void shouldReturnACashCardWhenDataIsSaved() {
        ...
        assertThat(amount).isEqualTo(123.45);
    }
    ```

4.  Run the test again to ensure it passes.

    ```dashboard:open-dashboard
    name: Terminal
    ```

    ```shell
    [~/exercises] $ ./mvnw  test -Dtest=CashCardApplicationTests#shouldReturnACashCardWhenDataIsSaved
    ```

    The output should look similar to the following:

    ```shell
    [INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 10.012 s - in example.cashcard.CashCardApplicationTests
    ```

    Our test passes!

5.  Re-run all the tests.

    Let's rerun all tests to ensure everything is passing.

    ```dashboard:open-dashboard
    name: Terminal
    ```

    ```shell
    [~/exercises] $ ./mvnw  clean test
    ```

    All the tests should now be passing with no `skipped tests`.

    ```shell
    [INFO] Tests run: 19, Failures: 0, Errors: 0, Skipped: 0
    [INFO]
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESS
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time:  8.531 s
    [INFO] Finished at: 2023-08-10T22:55:28Z
    [INFO] ------------------------------------------------------------------------
    ```

Now that everything is fixed it's time to baseline.
