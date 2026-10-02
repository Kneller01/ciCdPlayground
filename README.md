# The playground

This is intended to be a minimal project for a CI/CD workshop.
It consists of a simple JavaScript project, some unit and integration tests, and example configuration for some CI/CD tools.

## Setup

Yarn is recommended, but corresponding npm commands should work, too.

To install dependencies run `yarn`

Serve at localhost:8081 with `yarn dev`

Run tests with `yarn test` and `yarn test:e2e`

## CI test results

The GitHub Actions CI workflow publishes Jest and Cypress JUnit results in the
workflow run's job summary and a **Test results** check, even when tests fail.
Fork and Dependabot pull requests receive the job summary only because their
tokens cannot write checks. The XML reports are also available in the
**test-results** artifact. Only suites that ran are included; integration tests
are skipped if unit tests or the build fail.

**NOTES**:

- For participants:
  Pease check the preparation notes in Confluence. That's all you need to know, but of course you are welcome to look around.
- For organisers:
  There is some more info in `organiser_notes.md`.
