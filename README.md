# Git Commitizenship

The presentation slides are available in [docs](docs).

Additional docs include a Conventional Commits cheat sheet, the demo install script, and a Vi/Vim editor message template to help decisioning on the commit message.

## Java Easter Egg

The project's POM file includes a project profile that can be used to execute `npm install` without having ask team members to run the command, or even install `node/npm`. 

`mvn -P husky clean verify` is enough.

### `activeByDefault`

It's even possible to make this profile a default. Just add the following following the `id` element:

```xml
...
<profile>
  <id>husky</id>
  <activation>
    <activeByDefault>true</activeByDefault>
  </activation>
  ...
```
## GitLab CI/CD Presentation

My previous RVASDUG presentation has [a repository](https://gitlab.com/another15y/rva-sdug-redux) and [a YouTube video](https://youtu.be/GD_tBUf6sno).

The YouTube video compliments this presentation showing how commit messages can inform your pipeline and releases.
