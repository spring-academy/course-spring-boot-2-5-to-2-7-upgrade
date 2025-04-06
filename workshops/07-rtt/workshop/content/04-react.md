Let's add a new section for the upgrade to the `upgrade-notes.md` file:

```editor:open-file
file: ~/exercises/upgrade-notes.md
```

```markdown
## Test Dependency Housekeeping

- Remove explicit version of `assertj-core`
```

### There's nothing more to do here!

... _or is there?_

As stated previously, the Spring Maintainers endeavor to manage these commonly used third-party libraries for you, that includes managing the whole dependency and not just its version.

Let's repeat what we just did, but for the dependency, not just it's version.
