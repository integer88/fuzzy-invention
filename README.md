# fuzzy-invention
Just a test repo to make some github actions tests

## Release Workflow

The `release.yml` workflow is a GitHub Actions workflow that is triggered when a tag matching the pattern 'V\d.\d.\d' (e.g., V1.0.0) is pushed to the repository.

The workflow consists of three jobs:

1. `extract-version`: This job runs on an Ubuntu runner. It has two steps:
   - `Extract version`: This step extracts the version number from the tag (removing the 'V' prefix) and sets it as an environment variable.
   - `Echo version`: This step prints the extracted version number to the console. The version number is also set as an output of the job so it can be used in subsequent jobs.

2. `echo-version-ubuntu`: This job also runs on an Ubuntu runner. It depends on the `extract-version` job and will not run until `extract-version` has completed successfully. It has one step:
   - `Use VERSION`: This step prints the version number (extracted in the `extract-version` job) to the console.

3. `echo-version-windows`: This job runs on a Windows runner. Like `echo-version-ubuntu`, it also depends on the `extract-version` job. It has one step:
   - `Use VERSION`: This step prints the version number (extracted in the `extract-version` job) to the console.

The purpose of this workflow is to demonstrate how to extract a version number from a tag and use it in subsequent jobs in a GitHub Actions workflow.
