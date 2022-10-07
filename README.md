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
    secrets:
      CLIENT_ID: ${{ secrets.CLIENT_ID }} # required (can be set in your repository settings)
```

## Usage
You just have to copy the [example workflow](example.yml) into the `.github/workflows` directory of your project and adjust the sections `with` and `secrets` to your needs. (Triggers can be adjusted as well, but the example should be fine for most projects.)

## Useful Links
- [labwork-docker](https://github.com/johndoe31415/labwork-docker): Docker image used for the pipeline
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Workflow Documentation](https://docs.github.com/en/actions/using-workflows/about-workflows)
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)

## Feedback
If you have any questions or suggestions, feel free to open an issue, create a pull request or contact me directly.
