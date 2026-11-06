# Coursework 1 (10%) Part 1. Preliminary Project

## Student Grade Management Program (Initial)

As a developer, you were asked to implement a student grade management program for Reboot College (a fictional university). As a first step, you need to implement the model classes with tests.

## Design

There are multiple ways to implement the program, but the university has provided a UML class diagram and specifications in this document.

Class Diagram

- The classes should be located in the package `uk.ac.rhul.cs2800.model`.
- You should place the exception classes in a separate package `uk.ac.rhul.cs2800.exception`.
- Getters & Setters are omitted in the diagram.
- The fields are omitted if the diagram shows the relationship between two classes.
  - For example, `Student` contains `private List<Grade>` as a field (please check the multiplicity annotation between `Student` and `Grade`).
- Please use `java.util.List` to handle multiple children in a class rather than `java.util.Map`.
- The `mnc` field in the `Module` class stands for "mandatory non-condonable".
- You should give meaningful names to the method parameters (they are named with single characters in the diagram only due to space constraints).
  - For example, `public void addGrade(Grade grade)`, not ~~`public void addGrade(Grade g)`~~.
- `NoGradeAvailableException` can be thrown if there is no grade available at all or not available for a specific module.
- `NoRegistrationException` can be thrown if a user tries to access grades for unregistered modules.
- `Registration.switchStatus` can throw a `NullPointerException` with the message `The target status hasn't been provided` if the status parameter is `null`.

## Requirements

- Your code **MUST** follow the [CS2800 Coding Standards](https://moodle.royalholloway.ac.uk/mod/resource/view.php?id=1371658).
- Before starting your task, you should write a GitLab issue that describes your task.
  - Your commits should mention the issue in the commit message.
- All your code MUST be written by following a proper Test Driven Development (TDD) process.
  - To demonstrate the TDD process, please add a brief comment to each test case, including the test order in which the tests were written.

```java
  @Test
  public void getAverageTest() throws NoGradeAvailableException, NoRegistrationException {
  // Test 1
    ...
  }

```

- All your code changes must be recorded in the `main` branch of your CS2800 repository in the department GitLab.
- As previously advertised, from the week following the first online lab session (i.e. week 3, starting 5 October), you should push commits to your repository every week.
  - We expect at least 5 commits (including any exercise commits) per week. A week runs from Monday to Sunday, inclusive.

## Validation

You can validate your code using the following steps.

- Clone your GitLab repository in [NoMachine](https://linux.cim.rhul.ac.uk/)
  - Please note that you are allowed to use NoMachine only for validation, not for main tasks.
- In your `CW1` folder, the command below should be executed without any errors in a terminal:

```bash
$ mvn compile test checkstyle:check spotbugs:check verify site
```

- Markers will configure your project with the model `pom.xml` file presented in [the CS2800 coding standards](https://moodle.royalholloway.ac.uk/mod/resource/view.php?id=1371658) and use the same command above to mark your coursework.
  - Even if your project can be executed with the above command without any errors, you will lose marks if your project is not compatible with the model configuration (see details below).
  - Customising the Maven configuration is allowed, but it is your responsibility to ensure that you can still run the command above with the model configuration without errors.

## Report

- You should write a report that answers the following questions:
  1. What software license do you want to use for your project?
  2. Please explain the main permissions and restrictions of the license you chose.
  3. Justify your choice of license based on your previous answer.
- The report must have a title page with your full name (Moodle name), student number, email address, and the URL of your GitLab repository.
- The report must be no more than two pages long, *excluding* the title page.
  - A penalty mark will be deducted if your report is too long (i.e. more than two A4 pages).
- Reports MUST be submitted as a Portable Document Format (PDF) using A4 size, single-line spacing, and 12pt font.
  - Section headers and the title page can have a larger font size.
  - Reports that are not in this format **cannot and will not be graded**.

## Submission

### Moodle

- **You should submit a zip file containing your cloned repository folder and a report.**
  - The cloned repository folder is only for record-keeping; we will not grade it.

### GitLab

- All markings will be done based on the `main` branch of your CS2800 repository (i.e., `cs2800-202627/YOUR_USER_NAME`).
- **Please create a *tag* `CW1-submission` (case-sensitive) on the last commit for your coursework.**
- **Make sure all your commits were pushed to the department GitLab.**
  - Please double-check this by visiting the department [GitLab *website*](https://gitlab.cim.rhul.ac.uk/) and checking that you can see them.

## Feedback

Each student will get feedback comments for each grading section. Feedback will be delivered though the Moodle marking system.

## Marking Criteria

We have deployed a strong plagiarism detection algorithm. **DO NOT SHARE YOUR WORK WITH OTHERS!**

If you work on a repository that was not initialised by us, we will not grade your submission (i.e., you will get 0 marks).

Regardless of the quality of your final project, your mark will be **capped at 40** if your project:

- has no regular commits across each week
- contains less than 10 commits that make all changes

### Project Configuration (10 marks)

- A default issue template (`.gitlab/issue_templates/Default.md`) is correctly configured in your repository (2 marks).
- A default merge request template (`.gitlab/merge_request_templates/Default.md`) is correctly configured in your repository (2 marks).
- You should correctly set up build plugins as specified in the CS2800 coding standards (2 marks).
- You should correctly set up report plugins as specified in the CS2800 coding standards (2 marks).
- A meaningful `LICENSE` file is located at the root of repository (2 marks).
- If any of your code contains carriage return characters (`\r`), you will **lose 3 marks**.
- If your project is located in a folder other than the `/CW1`folder (case-sensitive), you will **lose 7 marks**.
  - A nested folder structure (i.e., `/CW1/CW1`) is not allowed.

### Use of Git & GitLab (20 marks)

- As described in the CS2800 Coding Standards, your commits should include less than 50 lines of changes on average.

| **Description**                                                                        | **Marks** |
| -------------------------------------------------------------------------------------- | --------- |
| `.gitignore` is correctly configured                                                   | 2 marks   |
| The `CW1-submission` tag has been crated and visible on GitLab                         | 3 marks   |
| Issues are well documented with the given template                                     | 0–5 marks |
| Merge requests are well documented with the given template                             | 0–5 marks |
| Commits have meaningful messages and are connected to GitLab issues and merge requests | 0–5 marks |

- You should regularly commit to your CS2800 GitLab repository.
- If your repository contains build artefacts (e.g., `targets`), project metadata (e.g., `.metadata`, `.classpath`, and `.settings`), and OS metadata (e.g., Windows: `Thumbs.db`, `[Dd]esktop.ini`, and `$RECYCLE.BIN` / macOS: `.DS_Store`), you will **lose 7 marks**.
- If your commits include more than 50 lines of changes on average, you will **lose 7 marks**.
- If you make a direct commit to the `main` branch after the initial commits (i.e., those made by following the Lab 1 materials), you will **lose 7 marks**.

### Does the code work? (10 marks)

Your code will be configured with the model `pom.xml` from the CS2800 Coding Standards and validated. With the given model configuration, your code should not show any error.

| **Description**                                                                       | **Marks** |
| ------------------------------------------------------------------------------------- | --------- |
| No Test Failures with your own configuration; failures occur with the model one       | 0 marks   |
| No Checkstyle Failures with your own configuration; failures occur with the model one | 0 marks   |
| No Spotbugs Failures with your own configuration; failures occur with the model one   | 0 marks   |
| No Compilation Error                                                                  | 1 marks   |
| No Test Failures with the model configuration                                         | 4 marks   |
| No Checkstyle Failures with the model configuration                                   | 4 marks   |
| No Spotbugs Failures with the model configuration                                     | 1 marks   |

### Javadoc (10 marks)

Your javadoc will be classified into one of the following five categories, and marked accordingly:

| **Description**                                                               | **Marks** |
| ----------------------------------------------------------------------------- | --------- |
| There are no comments or the existing commentx do not use the javadoc syntax. | 0 marks   |
| Several javadoc comments, but it still introduces checkstyle issues           | 2 marks   |
| Detailed javadoc comments, but contains checkstyle errors regarding javadoc   | 4 marks   |
| Reasonable javadoc comments without checkstyle errors                         | 6 marks   |
| Detailed javadoc comments without checkstyle errors                           | 10 marks  |

### Implementation (10 marks)

If your classes are not located in the packages `uk.ac.rhul.cs2800`, you will **lose 3 marks**.

| **Description**                                                     | **Marks** |
| ------------------------------------------------------------------- | --------- |
| You implemented all classes specified in the class diagram          | 0–2 marks |
| All relationships in the class diagram are correctly implemented    | 0–2 marks |
| The exceptions are properly thrown                                  | 0–2 marks |
| The public methods in the `Student` class are correctly implemented | 0–4 marks |

### Test Driven Development (TDD) (5 marks)

| **Description**                                                                                  | **Marks**                  |
| ------------------------------------------------------------------------------------------------ | -------------------------- |
| If any class has more than one failing test case                                                 | capped at 0 out of 5 marks |
| Each test must have a comment like `// Test 1` to show the order in which the tests were written | 0–1 marks                  |
| The progression of the tests must be reasonable for development                                  | 0–1 marks                  |
| If tests have obviously come before coding and the TDD step size looks appropriate               | 0–3 marks                  |

### Test Coverage (5 marks)

Assuming your project is correctly configured with the model configuration, marks will be given based on the test coverage:

One of the marks:

| **Test Coverage** | **Marks** |
| ----------------- | --------- |
| Test Failure      | 0 marks   |
| < 59%             | 1 marks   |
| 60%–89%           | 3 marks   |
| 90%–99%           | 4 marks   |
| 100%              | 5 marks   |

### License Report (30 marks)

Your license description will be classified into one of the five categories below, and marked accordingly:

| **Description**                                         | **Marks**                   |
| ------------------------------------------------------- | --------------------------- |
| No report about licensing included in the submission    | Capped at 0 out of 30 marks |
| Too brief description of the license and justification  | 0–8 marks                   |
| Reasonable description of the license and justification | 9–18 marks                  |
| Good description of the license and justification       | 19–25 marks                 |
| Very good description of the license and justification  | 26–30 marks                 |

### Bonus

- There will be bonus marks based on your checkpoint activities.
- Each checkpoint you pass is worth **1 bonus mark** (i.e., you will get up to 4 bonus marks if you pass all checkpoints.)
- Please note that the sum of your marks will be capped at 100 and will not carry over to the other components and Coursework 2. Also, You can earn the bonus grades during the term time only and they will only count for your first-sit (i.e., not available for SVAP).
- If you pass Checkpoints 1–4 after CW1 submission deadline, their bonus marks will NOT be counted for your CW1 (and CW2). **To get bonus marks, please make sure to pass them before the deadline.**