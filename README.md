# Bump-Go Action

This GitHub Action auto-creates a PR that bumps the Go version to the latest available stable version and updates the standard libraries in your project.

## Features

- Determines the current Go version from a specified file or direct version input.
- Checks if the current Go version is part of a major (stable) release.
- If the current Go version is not part of a major release, the action fails.
- If the current Go version is part of a major release but is not the latest patch version, the action bumps the Go version to the latest patch version.
- Updates all Go standard libraries to their latest versions.
- Commits these changes and pushes them to a new branch.
- Creates a pull request for these changes.

## Inputs

- `go_version`: The current Go version. The value can be a specific version (e.g., `1.22.3`) or a file containing the version (e.g., `.go-version`). Default: `.go-version`.
- `github_token`: The GitHub token used to create the pull request. The token needs `contents:write` and `pull-requests:write` permissions. Default: `${{ github.token }}`.
- `pr_reviewer`: The GitHub username of the reviewer assigned to the pull request.

## Usage

```yaml
- name: Bump Go version and update stdlibs
  uses: dduzgun-security/bump-go@v1
  with:
    go_version: .go-version
    github_token: ${{ secrets.GITHUB_TOKEN }}
    pr_reviewer: github-username
```

## Requirements

Be sure to have the `Allow GitHub Actions to create and approve pull requests` option enabled.
