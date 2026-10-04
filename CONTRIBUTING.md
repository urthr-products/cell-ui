# Contributing to cell-ui

Thank you for considering a contribution. cell-ui is maintained on a best-effort basis, so focused changes with clear motivation and tests are the easiest to review.

## Before you start

- Search existing issues and pull requests.
- Open an issue before large features or public API changes.
- Do not use public issues for security vulnerabilities; follow [SECURITY.md](./SECURITY.md).
- Keep formula engines and application-specific behavior outside the core unless the change extends the plugin API.

## Development setup

Requirements: Node.js 22.12.0 or later and npm.

```bash
git clone https://github.com/urthr-products/cell-ui.git
cd cell-ui
npm ci
npm run typecheck
npm test
npm run build
npx playwright install chromium
npm run e2e
```

## Pull requests

1. Create a branch from `main`.
2. Keep the change focused and avoid unrelated formatting.
3. Add or update tests for behavior changes.
4. Update English and Japanese documentation when user-facing behavior changes.
5. Run the verification commands above.
6. Explain the motivation, implementation and test results in the pull request.

By contributing, you agree that your contribution is licensed under the repository's MIT License.

## Review and acceptance

A submitted issue or pull request does not guarantee implementation, review or inclusion. Maintainers may close requests that are outside the project scope, insufficiently reproducible or likely to create disproportionate maintenance cost.
