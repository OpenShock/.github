# Contributing to OpenShock

Thank you for wanting to help. This guide applies to every repository in the OpenShock
organization. A repository may have its own `CONTRIBUTING.md` with build instructions and
conventions; where it does, that file takes precedence.

By taking part you agree to follow our [Code of Conduct](https://github.com/OpenShock/.github/blob/main/CODE_OF_CONDUCT.md).

## Ways to contribute

- **Report bugs and request features** in the issue tracker of the affected repository. Search
  for an existing issue first.
- **Improve the documentation** in the [Wiki repository](https://github.com/OpenShock/Wiki).
- **Help other users** on [Discord](https://discord.gg/OpenShock).
- **Contribute code** with a pull request.

See [SUPPORT.md](https://github.com/OpenShock/.github/blob/main/SUPPORT.md) if you are looking for help rather than looking to contribute.

## Security vulnerabilities

**Never report a security vulnerability in a public issue or pull request.** Follow the
[security policy](https://github.com/OpenShock/.github/blob/main/SECURITY.md) and report it privately. If you have already written a fix, do
not open a public pull request for it; mention it in your report and we will work on it with you
in a private fork.

## Pull requests

1. For anything larger than a small fix, open an issue or talk to us on Discord first, so that
   nobody builds something that cannot be merged.
2. Fork the repository and create a branch from its default branch.
3. Keep the change focused. One pull request should do one thing.
4. Follow the existing code style. Run the formatter, linter and tests the repository provides
   before pushing.
5. Add or update tests for behaviour you change.
6. Describe what the change does and why, and link the issue it resolves.
7. Make sure CI passes. A maintainer will review the pull request; expect questions and change
   requests.

Do not commit secrets, credentials or personal data. If you accidentally push one, tell a
maintainer immediately so it can be rotated; deleting the commit is not enough.

## Safety-relevant changes

OpenShock controls devices that people wear. Changes that touch device control, intensity or
duration limits, sharing and permissions, authentication, or firmware updates get extra scrutiny
in review. Please call out such changes in the pull request description and explain how you
tested them.

## Licensing

Contributions are accepted under the license of the repository you contribute to. By opening a
pull request you confirm that you have the right to submit the work under that license.

## Development setup

Each repository documents its own setup in its `README.md`. More guides are collected in the
[developer section of the Wiki](https://wiki.openshock.org/dev/contributing/).
