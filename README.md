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

## Contributing

Contributions are welcome and appreciated! Here's how you can contribute:

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

Please make sure to update tests as appropriate and adhere to the existing coding style.

## License

This project is licensed under the CSSM Unlimited License v2.0 (CSSM-ULv2). See the [LICENSE](LICENSE) file for details.
