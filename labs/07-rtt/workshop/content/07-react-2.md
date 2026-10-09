This time our **r**eaction is to simply note the change in the `upgrade-notes.md` file.

Modify the contents in the `Test Dependency Housekeeping` section:

```editor:open-file
file: ~/exercises/upgrade-notes.md
```

```markdown
- ~~Remove explicit version of `aspectj-core`~~
- Remove explicit `aspectj-core` dependency
  - It's managed by `spring-boot-starter-test`

_Result:_ code compiles without errors or warnings and all tests pass
```
