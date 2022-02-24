# Action to create new Releases based on a keyword
The Keyword Releaser will creates a new Release based off of a keyword specified in the arguments of an action

# Environment Variables
- `GITHUB_TOKEN` - _Required_ Allows the Action to authenticte with the GitHub API to create the release.

# Arguments
- _Required_ - A single keyword.  If the keyword is found in a commit message, a release will be created.  The keyword is not case-sensitive, however its recommended it be a unique, uppercase string such as `FIXED`, or `READY_TO_RELEASE`.

# Examples
Here's an example workflow that uses the Keyword Releaser action.  The workflow is triggered by a `PUSH` event and looks for the keyword `"FIXED"`.

```
name: keyword-releaser

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v1
    - uses: automate6500/keyword-release-action@master
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        args: 'FIXED'
```

