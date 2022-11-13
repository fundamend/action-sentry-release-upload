# action-sentry-release-upload

_action-sentry-release-upload_ is a workflow for [GitHub Actions] used by the [fundamend.dev] ecosystem.
It creates a new [Sentry] release and uploads the corresponding sourcemaps.

## Usage

In your package, create a workflow that uses _action-sentry-release-upload_, like so:

```yaml
name: Release

on: [push]

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Sentry Release Upload
        uses: fundamend/action-sentry-release-upload@main
        with:
          environment: 'preview'
          sentry-auth-token: ${{ secrets.SENTRY_AUTH_TOKEN}}
          sentry-organization: 'test-org'
          sentry-project: 'test-app'
          sourcemaps-path: 'dist'
          build-command: 'npm run build'
          working-directory: './subfolder'
```

The action takes the following inputs:

| Key                      | Description                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------ |
| `environment`            | The environment of the release (default `production`)                                |
| `sentry-auth-token` \*   | Your Sentry auth token                                                               |
| `sentry-organization` \* | Your Sentry organization that contains the project                                   |
| `sentry-project` \*      | Your Sentry project to which the release and uploads should be added                 |
| `sourcemaps-path`        | The path to your sourcemaps (default `build`)                                        |
| `build-command`          | The build command to be used to create the sourcemaps (default `npm run prod`)       |
| `working-directory`      | The directory where from where build and upload commands should be run (default `.`) |

The \* indicates mandatory inputs.

## License

[MIT]

[fundamend.dev]: https://fundamend.dev
[github actions]: https://docs.github.com/en/actions
[github]: https://github.com/
[mit]: https://choosealicense.com/licenses/mit/
[sentry]: https://sentry.io
