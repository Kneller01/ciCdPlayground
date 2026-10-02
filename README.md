# The playground

This is intended to be a minimal project for a CI/CD workshop.
It consists of a simple JavaScript project, some unit and integration tests, and example configuration for some CI/CD tools.

## Setup

Yarn is recommended, but corresponding npm commands should work, too.

To install dependencies run `yarn`

Serve at localhost:8081 with `yarn dev`

Run tests with `yarn test` and `yarn test:e2e`

## CI test results

The GitHub Actions CI workflow uses `dorny/test-reporter` to publish Jest and
Cypress JUnit reports as **Unit test results** and **Integration test results**
checks, including when tests fail. Only suites that ran are reported; integration
tests are skipped if unit tests or the build fail. Reporting is skipped for fork
and Dependabot pull requests because their tokens cannot write checks.

## GitHub Pages

Set **Settings > Pages > Build and deployment > Source** to **GitHub Actions**.
The existing **CI** workflow publishes the built `public` directory to GitHub
Pages after the build and tests succeed on `master`. Pull requests and other
branches run CI without deploying.

Publication is enabled by default. To disable it, create a repository variable
named `DEPLOY_PAGES` with the value `false` under **Settings > Secrets and
variables > Actions > Variables**. Set it to `true` or delete the variable to
re-enable publication. Disabling publication skips Pages configuration, artifact
upload, and deployment, but still runs the build and tests. It does not remove
the already published site.

Commit and push changes to `master` to publish, or select **Actions > CI > Run
workflow** and choose `master` to redeploy manually.
Changing the variable does not trigger a workflow run.
The site is available at <https://kneller01.github.io/ciCdPlayground/>.

**NOTES**:

- For participants:
  Pease check the preparation notes in Confluence. That's all you need to know, but of course you are welcome to look around.
- For organisers:
  There is some more info in `organiser_notes.md`.
