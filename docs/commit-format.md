---
mainfont: gillius
---

# The Basic and Default Commit Format

```text
<type>(<optional scope>): <imperative-subject-line>
empty separator line
<optional body>
empty separator line
<optional footer>
```

## Types
* API relevant changes
    * `feat` commits add a new feature
    * `fix` commits fix a bug
* `docs` commits are documentation only
* `style` commits SHOULD not affect the meaning (white-space, formatting, missing semi-colons, etc.)
* `refactor` commits code changes that neither fixes a bug (`fix`) nor adds a feature (`feat`)
* `perf` commits improve performance
* `test` commits add missing tests or correcting existing tests
* `build` commits affect the build system or external dependencies
* `ci` commits CI configuration files and scripts
* `chore` commits include changes that don't modify `src` or test file, e.g., `.gitignore` changes
* `revert` commit, well, revert a previous commit. 

**Only** `feat` and `fix` generate a release, minor and patch, respectively. A [`footer`](#footer) will generate a major
release, *only* if containing the defined markers of Conventional Commits, as follows:

```text
feat(api): new REST resource for PATCHing

Deprecate PUT for PATCH, supporting full resource replacement in an HTTP-compliant manner.

BREAKING CHANGE:

PUT returns 410 Gone with a Sunset header of Sat Mar 23 21:41:57 EDT 2024.
```

The commit subject MAY use an `!`, i.e., `feat(api)!: new REST resource for PATCHing`. This form generates a Major release, i.e., a breaking change, and the commit subject recorded in the CHANGELOG.
