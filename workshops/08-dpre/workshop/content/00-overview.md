Up to this point we've discussed the evolution of Spring Projects over time. We've addressed dependency issues, code issues and deprecations, etc.

Like how the code evolves, so has Spring's capability to manage configuration from external sources.

Property names will change over time. To assist with this migration, the Spring Maintainers have produced a library, `spring-boot-properties-migrator`, that will inspect your property configuration and provide you with errors and warnings based on the nature of change to the property itself.

The `spring-boot-properties-migrator` is a **DEVELOPMENT ONLY** library! The intention is to run the application locally, capture the output, address the needed property changes, then remove (or comment out the dependency for future use).

This sounds an awful lot like the **SCAR** method, doesn't it?

## Review our Upgrade Notes

Before we begin, remember that we're keeping detailed notes of the baseline state of our application as we upgrade it. Take a look at `upgrade-notes.md` to review where we are now.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```
