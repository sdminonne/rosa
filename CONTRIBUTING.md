# Contributing to ROSA
Welcome, and thank you for considering to contribute to ROSA.
Before you begin, or have more questions reach out to us on [Slack](https://redhat-internal.slack.com/archives/CB53T9ZHQ)

## Contributing Code
To contribute bug fixes or features to ROSA:

- Communicate your intent.
- Make your changes.
- Test your changes.
- Open a Pull Request (PR).

Communicate your intent in the form of a JIRA ticket on the [Service Development A](https://issues.redhat.com/projects/SDA/summary) board.
All JIRA's are refined by the team on a weekly cadence.

Be sure to practice good git commit hygiene as you make your changes. All but the smallest changes should be broken up
into a few commits that tell a story. Use your git commits to provide context for the folks who will review PR. We strive
to follow [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/#summary).

The commit message should follow this template:
```shell
<type>[JIRA-TICKET] | [TYPE] : <MESSAGE>

[optional BODY]

[optional FOOTER(s)]
```

The commit contains the following structural types, to communicate your intent:

- `fix:` a commit of the type fix patches a bug in your codebase (this correlates with PATCH in Semantic Versioning).
- `feat:` a commit of the type feat introduces a new feature to the codebase (this correlates with MINOR in Semantic
  Versioning).

Types other than `fix:` and `feat:` are allowed:
- `build`: Changes that affect the build system or external dependencies
- `ci`: Changes to our CI configuration files and scripts
- `docs`: Documentation only changes
- `perf`: A code change that improves performance
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- `test`: Adding missing tests or correcting existing tests

All code should be covered by tests. We use [Ginkgo](https://onsi.github.io/ginkgo/). Other third party testing package
will be rejected.

Once you made and tested your changes, create a pull request (PR). In the PR `overview` please link the
jira ticket associated with your change. This should follow the format `JIRA: SDA-xxxx`. Note the key word `JIRA`,
use of any other key word may result in the bot performing unwanted action to the ticket in JIRA. Please also include in the
`overview` any additional information not in the JIRA that may help set context around your intent. Also include any extra
validation steps which may help reviews to validate the changes.

We work on a Sprint basis, all changes should be tracked by a JIRA. When being worked on these changes should be added to
the current SDA sprint. These sprints are denoted as `SDA - Sprint xxx`. The workflow should be as follows:
- `Todo` will complete in this current sprint
- `In Progress` ticket is currently being worked on
- `Code Review` PR has been created and is being reviewed by the team.
- `Review` Once the changes have been merged, move ticket to `Review` a QE person will be assigned to the ticket and tested.
- `Done` Once QE are satisfied with the change and bugs have been fixed the QE person assigned to your ticket will mark it
  as done

During `Review`, remain assigned to the ticket, so that QE knows who to assign any follow-up bugs to during testing. You
will also be asked to review test cases for this change. QE will supply you with a link to the test cases, if you approve
the test cases add `tc-approved` label to the JIRA, if you need changes to the test cases work with QE in the JIRA comments
to resolve these changes.

# CI
## Prow

This repository is using Prow CI running at https://prow.ci.openshift.org/,
configured in https://github.com/openshift/release repo.

`.golangciversion` file is read by the `lint` job commands there:
https://github.com/openshift/release/blob/master/ci-operator/config/openshift/rosa/openshift-rosa-master.yaml

## GitHub Workflows

This repository also uses GitHub actions which are configured at `./github/workflows`

# Questions?

If you have any questions about the code or how to contribute, don't hesitate to
[open an issue](https://github.com/openshift/rosa/issues/new) in this repo