# File Notes

## .gitmessage

This is my personal Git Commit message template. This template is used by Git to populate a commit and provides hints
on using Conventional Commits properly.

To use it:

`git config --add commit.template path/to/.gitmessage` where `path/to` MAY be your user home directory, or other
location that you store curated development files.

## commit-format.md

This is a cheat sheet in Markdown. Print and hang in view of your workstation. Share. Laminate.

## scripts/skip_tests.sh

This is a simple shell script that outputs a helpful hint about skipping Maven tests on 
commit. If the project's test suite is extensive and takes any more than a couple of minutes, running tests on commit might be impede atomic commit practices.

### Husky

`npx husky init` sets the default `pre-commit` script to `npm test`. This requires the presence of a run script called `test`, which must be present in the `package.json`. So the project provides one for completeness, with some additional elements for a robust example.

### Skipping Tests on Commit

The NPM `test` run script is set as follows:

`"test": "npm run info:skip-tests && mvn clean test ${SKIP_TESTS+-Dmaven.test.skip=true}"`

The first part outputs a reminder. The final part runs the Maven `test` lifecycle, but will skip the tests if `-Dmaven.test.skip=true` is present. 

#### Options

1. Set an environment variable in your shell environment, i.e., `export SKIP_TESTS="true"`.
2. Set an ephemeral environment variable in the terminal, i.e., `% export SKIP_TESTS="true"`.\
🚨 This will disappear when closing the current terminal.
3. Set a command environment variable, i.e., `SKIP_TESTS="true" git commit --all --verbose`.
