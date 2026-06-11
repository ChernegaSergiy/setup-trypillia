# Setup Trypillia

A GitHub Action to set up the Trypillia programming language environment. It automatically builds the Trypillia compiler natively and adds it to your `$PATH`.

## Usage

Use this action in your GitHub Actions workflows to easily run Trypillia scripts or tests.

```yaml
name: Trypillia CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Trypillia
        uses: ChernegaSergiy/setup-trypillia@v1
        with:
          version: 'latest'
          
      - name: Run Tests
        run: trypillia test.try
```

## How it works

Because Trypillia is currently compiled from source, this composite action will:
1. Clone the `trypillia-language` repository.
2. Build it using `cmake` and `make`.
3. Copy the compiled `trypillia` binary to `$HOME/.local/bin` and expose it to the `$GITHUB_PATH`.

*Note: In the future, this action will download pre-compiled binaries to speed up execution.*
