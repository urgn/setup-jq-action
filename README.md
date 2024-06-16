# setup-jq-action
GitHub Action to setup the `jq` command for json parsing

Example of use :
```yaml
name: Release

on: [ "push" ]

jobs:
  parse_yaml:
    name: Parse JSON
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Install jq
        id: setup-jq
        uses: urgn/setup-jq-action@v3.0.2
      - name: get version
        run: |
          VERSION=$(${{ steps.setup-jq.outputs.jq-binary }} '.dependency.my_component.git.ref' pubspec.json)
```
