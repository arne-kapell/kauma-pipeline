# KAuMA Pipeline
Reusable GitHub workflow for KAuMA projects at DHBW Mannheim.

Can be referenced in your own workflow (see [Usage](#usage)):
```yaml
jobs:
  reusable-pipeline:
    uses: arne-kapell/kauma-pipeline/.github/workflows/pipeline.yml@main
    with:
      TEST_SERVER: 'https://dhbw.johannes-bauer.com/lwsub/' # optional (default: https://dhbw.johannes-bauer.com/lwsub/)
      DEFAULT_ASSIGNMENT: 'labwork01' # optional (default: labwork01)
      CONTAINER_TIMEOUT: 30 # optional (default: 30)
      IMAGE_TAG: 'master' # optional (default: nightly)
    secrets:
      CLIENT_ID: ${{ secrets.CLIENT_ID }} # required (can be set in your repository settings)
```

## Usage
You just have to copy the [example workflow](example.yml) into the `.github/workflows` directory of your project and adjust the sections `with` and `secrets` to your needs. (Triggers can be adjusted as well, but the example should be fine for most projects.)

IMPORTANT: Please don't forget to set your `CLIENT_ID` in GitHub Secrets (can be found in Repository settings)!

### Current assignment
The pipeline looks for which assignment to run the container with in `.current_assignment` in your repository root. You can then just change its value for moving on to the next assignment *(everything but the first line will be ignored)*. If this file can't be found/read the `DEFAULT_ASSIGNMENT` is used.

### Past assignments (optional)
If you want to run the pipeline for past assignments, you can create a file `.past_assignments` in your repository root. It should contain a list of all past assignments, **one per line**. The pipeline will then run the container for each of these assignments as well.

## Common problems

### run/build scripts not executable
The pipeline checks if the scripts `run` and `build` are executable. If they aren't, it will not try to make them executable. You can do this manually by using the commands below:
```bash
git ls-files -s <run/build>
# if the output starts with something like "100644" (without the quotes), the file is not executable
git add --chmod=+x <run/build>
git ls-files -s <run/build>
# if the output starts with something like "100755" (without the quotes), the file is now executable
git commit -m "Made <run/build> executable"
git push
```
*Don't forget to replace `<run/build>` with the actual file name (without the brackets)!*

### Container timeout
If the container times out, you can increase the timeout by setting the `CONTAINER_TIMEOUT` input to a higher value. The default is `30` seconds.

## Useful Links
- [labwork-docker](https://github.com/johndoe31415/labwork-docker): Docker image used for the pipeline
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Workflow Documentation](https://docs.github.com/en/actions/using-workflows/about-workflows)
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)

## Feedback
If you have any questions or suggestions, feel free to open an issue, create a pull request or contact me directly.
