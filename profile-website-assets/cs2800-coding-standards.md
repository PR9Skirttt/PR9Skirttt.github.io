# CS2800 Coding Standards

This document describes the coding standard of CS2800 Software Engineering. Your work within the module should follow the exercise described here.

## Maintainable Code

The definition of `maintainable code` in this module is that the code satisfies all the criteria below:

- You should use Maven to manage your project. All dependencies, static analysers, and configurations should be managed by Maven.
- A Maven project with the configurations presented in the later document, including dependencies and build & report plugins.
- A Maven project with the correct configuration to execute the below command in a terminal without any errors:

```bash
$ mvn compile test checkstyle:check spotbugs:check verify site
```

- Your code style should follow the code styles described later in this document
- Your projects (e.g., Coursework and Lab materials) in CS2800 should use the root package name of `uk.ac.rhul.cs2800`.
- You should use **JDK 25** or later releases that are compatible with JDK 25.
- For unit tests, you should use JUnit 5, JUnit 4 or lower versions are not allowed.
- All your projects must achieve the test coverage of **90% or higher**.

### Static Analysers

Your project should be configured with three static analysers. You can find an example configuration later in this document.

- **Checkstyle**: It warns you if you violate any coding styles documented here.
- **Spotbugs**: It warns you common mistakes by developers. For this module, you can use `High` severity which is not super sensitive.
- **JaCoCo**: It includes test coverage information in the project report.

## Git

- All your work should be regularly committed to your repository which is initialised in the department GitLab instance.
  - "Regularly" means at least five commits per week.
  - Commits do not necessarily code changes, but can be anything (e.g., commit exercise and documentation)
  - Just make sure you don't break the coding standards in the repository.
- The default branch name is `main`.
- Direct commit to `main` is not allowed.
- You should properly configure `.gitignore` in your repository, so unnecessary artefacts (e.g., `target`, `.settings`, and `node_modules`) should not be added to your repository
  - You can generate one here: [https://gitignore.io](https://gitignore.io/)
  - If you already added unnecessary files in your repository, please remove them.
- You should properly configure `.gitlab-ci.yml` in your repository, so every commits will be validated.
  - You don't need to worry about this configuration before we cover continuous integration in lab session.
- We expect **at least 5 commits** per week.
- **On average, commits should include fewer than 50 lines of changes.** If a change is larger than that, split it into multiple commits.
  - The number of changed lines = the number of added lines - the number of deleted lines
  - For example, you have two commits:
    - A commit adds 30 lines and deletes 18 lines, it changed 12 lines.
    - A commit adds 10 lines and deletes 16 lines, it changed -6 lines.
    - Then, the average of changed lines is +3 lines.
- Your commit message should start with a hashtag that points to a GitLab issue.
- You should push your commits every week during the term time.

### Issue Template

- You must configure this issue template in your repository
- You can save this template at `.gitlab/issue_templates/Default.md`

```xml
## What needs to be done

<!-- Describe the task in one or two sentences, or as a few bullet points. -->

## Done When

<!-- How will you know the task is finished? -->

/assign me
```

### Merge Request Template

- You must configure this merge request template in your repository
- You can save this template at `.gitlab/merge_request_templates/Default.md`

```xml
## What changed

<!-- One or two sentences -->

## Checklist

- [ ] Made less than 50 lines changes
- [ ] `mvn compile test checkstyle:check spotbugs:check verify` work
- [ ] CI Pipeline Passing

## Use of AI tools

- [ ] No AI tools used
- [ ] AI tools used — tool(s): ______ ; for what: ______ ; how I checked the output: ______

/assign me
```

## Best Practice

- Write an issue on GitLab and assign yourself to it before you start a task.
  - At any stage, please use comment to take a note of some context you want to record.
- Make your local repository up to date: `git pull`
- Create and checkout a branch in your local repository: `git checkout -b [BRANCH_NAME]`
- Make changes
- Evaluate your changes with the above maven command.
- If everything is okay, stage your changes : `git add .`
  - By adding the current path, we assume you correctly configured a gitignore at the root of your repository.
  - Otherwise, it will add unnecessary files.
- Create a commit: `git commit -m "#ISSUE_ID DESCRIPTIVE_COMMIT_MESSAGE"`
- Push your commit to GitLab: `git push origin [BRANCH_NAME]`
- Go to GitLab on browser and create a merge request.
- Review your change.
- If you think a change is required, create a commit locally and update the merge request.
- If the commit looks good and CI passes, merge it.
- Close the issue.

## Coding Styles

- Do not use tab characters for indentation
- The unit of indentation is 2 spaces.
- Method and variable names should use lower camel case (e.g., `private String helloWorld`).
- Class names should use upper camel case (e.g., `class HelloWorld`).
- Package names should use only lower case letter and digits.
- All constant variables should use screaming snake case (upper snake case) (e.g., `private static final String HELLO_WORLD`).
- There should be no Checkstyle violations with the [Checkstyle configuration for 'Google Java Style'](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/google_checks.xml).

Any code style issues that are not listed here, you should follow [Google Java Style](https://google.github.io/styleguide/javaguide.html).

## Repository Structure

All these files and folder names are case-sensitive.

```undefined
ROOT_OF_YOUR_REPOSITORY
├── .gitignore
├── .gitlab
    ├── issue_templates
    │   └── Default.md
    └── merge_request_templates
        └── Default.md
├── .gitlab-ci.yml
├── LICENSE
├── README.md
├── AI.md
├── CW1
├── CW2
└── Lab
```

- `.gitignore`: The list of files you exclude in your commits. Using [https://gitignore.io](https://gitignore.io/) to generate the file is recommended
- `.gitlab`: A folder can store [issue and merge request templates](https://gitlab.cim.rhul.ac.uk/help/user/project/description_templates). You can find the templates above.
- `.gitlab-ci.yml`: Continuous integration configuration. It is only required after the CW1 submission.
- `LICENSE`: The license of your project.
- `README.md`: A markdown file explains your repository.
- `CW1`: This directory should contain a maven project for CW1
- `CW2`: This directory should contain a maven project for CW1
- `Lab`: You can exercise the lab materials in this folder.
- `AI.md` (optional): If you use generative AI tools for your coursework, please write your statement in this file.
  - Please check the [coursework submission guidelines](https://moodle.royalholloway.ac.uk/mod/page/view.php?id=1113061) regarding the details of the statement.

For the `CW1` and `CW2` folders, they should contain a single maven project as below:

```css
CW2
├── pom.xml
└── src
    ├── main
    │   ├── java
    │   │   └── uk
    │   │       └── ac
    │   │           └── rhul
    │   │               └── cs2800
    │   │                   └── ** Sub-packages and java files **
    │   └── resources
    └── test
        ├── java
        │   └── uk
        │       └── ac
        │           └── rhul
        │               └── cs2800
        │                   └── ** Sub-packages and java files **
        └── resources
```

For `CW1`, you may don't need the `resources` folder

You can check the [example repository](https://gitlab.cim.rhul.ac.uk/cs2800/cs2800-example) for example.

## Recommended Development Environment

### Terminal

- Your project should be successfully compiled and tested in a terminal.
- Do not use a console or terminal that is embedded in an IDE.
- If you use MS Windows, you can use command line, but using [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) is highly recommended.
  - If WSL does not work on your machine, please consider [installing Ubuntu alongside with your Windows](https://canonical-ubuntu-desktop-documentation.readthedocs-hosted.com/en/latest/tutorial/install-ubuntu-desktop/) or using [VirtualBox](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox) to install Ubuntu.
- If you are not familiar with shell commands, please check [the missing semester of your cs education](https://missing.csail.mit.edu/)
- Using [starship](https://starship.rs/) to display diverse information is recommended.
  - You can find an example configuration here: [https://gitlab.cim.rhul.ac.uk/-/snippets/46](https://gitlab.cim.rhul.ac.uk/-/snippets/46)

### JDK

- Multiple vendors provide JDK, feel free to select one which compatible with the coding standards.
- Using [OpenJDK](https://openjdk.org/) is advisable. You can directly download OpenJDK from their website.
- (Recommended) You can install OpenJDK via [SDKMAN](https://sdkman.io/)
  - Once you install SDKMAN, you can install JDK via the command in terminal: `sdk install java 25-open`

### Maven

- The recommended Maven version is 3.9.16.
- You can download Maven from the [website](https://maven.apache.org/) and install it.
- (Recommended) You can install Maven via [SDKMAN](https://sdkman.io/) as well
  - You can run `sdk install maven 3.9.16` to install maven.
  - You can run `sdk default maven 3.9.16` to configure the default maven version.

### Node.js

- You can download Node.js from the [website](https://nodejs.org/) and install it.
- (Recommended) You can install nodejs via [Node Version Manager (nvm)](https://github.com/nvm-sh/nvm)
  - Once you install `nvm`, you can install Node.js via the command in terminal: `nvm install lts/krypton`
  - You can run `nvm alias default lts/krypton` to configure the default node version.

### [Eclipse](https://www.eclipse.org/downloads/packages/)

- Download [eclipse-java-google-style.xml](https://github.com/google/styleguide/blob/eaa0a05ec282e893ba314f1e6aeb9ef9f6674249/eclipse-java-google-style.xml) and import the configuration at `Preferences>Java>Code Style>Formatter`
- Enable `Insert spaces for tabs` under `Preferences>General>Editors>Text Editors`
- Check `Perform the selected actions on save` under `Preferences>Java>Editor>Save Actions`
  - Then, tick `Format source code` and `Format edited lines`

If you want to use an IDE other than Eclipse, you should configure the IDE by yourself to align with the above rules.

### Maven

- An example of `pom.xml`. You need to update `artifactId` and `name`.
- You can simply copy and paste this file.