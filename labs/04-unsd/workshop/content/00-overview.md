Some further `pom.xml` housekeeping to be mindful of. Spring will manage the dependency version for certain third-party dependencies. If you notice there are explicit versions for these dependencies, they should be removed.

There are also third-party libraries that Spring has no governance over. It is considered a _Best Practice_ to isolate these versions to Maven Properties, rather than inline the version with the dependency. This is a cleanliness task and helps to provide a visual reference to others the version of third-party libraries explicitly used in the application.

The one caveat here is around overriding Spring-managed third-party dependency versions explicitly. You may, for instance, have become aware of a CVE affecting a Spring-managed third-party library. You may also have found that the maintainers of that library have issued an update to that library, but Spring has no knowledge of it yet. In this case, its acceptable to override the version managed by the Spring Boot Parent, but you should follow the same rules as outlined for independent third-party libraries.

Let's get started and update non-Spring dependencies!

## Review our Upgrade Notes

But, before we begin, remember that we're keeping detailed notes of the baseline state of our application as we upgrade it. Take a look at `upgrade-notes.md` to review where we are now.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```
