We're not going to **C**ompile the code directly at this point. Rather, we are going to use the Spring Boot Maven Plugin to start the application.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw spring-boot:run
```

The application should be up and running, but you'll find some interesting output at the end of the log.

```shell
2023-08-17 09:40:05.832  INFO 73556 --- [           main] example.cashcard.CashCardApplication     : Started CashCardApplication in 5.026 seconds (JVM running for 5.474)
2023-08-17 09:40:05.836  WARN 73556 --- [           main] o.s.b.c.p.m.PropertiesMigrationListener  :
The use of configuration keys that have been renamed was found in the environment:

Property source 'Config resource 'class path resource [application.yml]' via location 'optional:classpath:/'':
        Key: spring.mvc.locale
                Line: 10
                Replacement: spring.web.locale


Each configuration key has been temporarily mapped to its replacement for your convenience. To silence this warning, please update your configuration to use the new keys.
```

Interesting! Let's keep track of this.
