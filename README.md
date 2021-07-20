# java-root-parent

This is root java parent pom which does/have: 
- have default configuration for maven-compiler-plugin for jdk 8 and 11
- contains profiles for release to maven repository
- it run verification of code style/issues via spotbugs/codenarc/pmd/checkstyle
- create flatten pom
- attach dependency lombok, commons-collections4, commons-io, commons-lang3
- contains dependencyManagement for junit, javafaker, assertj-core, mockito-core, groovy-all, cglib-nodep, objenesis, spock-core, spock-spring
- contains few profiles like: 
  - skip-code-review - it skips run code review via spotbugs/codenarc/pmd/checkstyle
  - coverage - it run code coverage done by jacoco-maven-plugin and coveralls-maven-plugin
  - release - it runs plugins like maven-gpg-plugin, nexus-staging-maven-plugin, maven-source-plugin, maven-javadoc-plugin during release to remote maven repository

required to override from child pom
```xml
<!-- required to override -->
        <release.project.name>your project name</release.project.name>
        <release.project.description>your project description</release.project.description>
        <release.project.repository-name>your repo name</release.project.repository-name>
        <coveralls.repo.token>coveralls token here</coveralls.repo.token>
```

not required to override from child pom but can be overriden:

```xml
<!-- not required to override -->
        <java.version>11</java.version>
        <coverage.exluded.classes>**/*Main.class</coverage.exluded.classes>
        <coverage.module.minimum>0.0</coverage.module.minimum>
        <release.project.repo-owner>github.com/mikolajmitura/</release.project.repo-owner>
        <release.project.repository-url>${release.project.repo-owner}/${release.project.repository-name}</release.project.repository-url>
```
