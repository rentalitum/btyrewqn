# btyrewqn

`btyrewqn` is a stand-alone React Native (Expo) wallet for the Stellar Testnet. It focuses on a polished, usable experience for core wallet flows while the underlying Stellar/Soroban tooling keeps evolving.

## Project Status

- This project is a polished but still-evolving wallet experience rather than a production-ready product.
- Core flows such as wallet creation and import, balance checks, sending and receiving, contacts, and the vault UI are implemented and actively refined.
- The app is intentionally focused on Stellar Testnet for development and experimentation. Testnet XLM has no real monetary value.
- The vault experience is currently mock-backed by default. A real Soroban contract integration can be enabled with configuration, but the default experience remains a safe placeholder.

> ⚠️ **This app runs on the Stellar Testnet only.** Testnet XLM has no real monetary value. Read the [Security Guide](docs/security.md) before storing or sharing any keys.

## Features

- Wallet creation and import
- XLM balance and transactions
- Send and receive with QR codes
- Address book contacts
- Soroban Savings Vault (dual-mode: mock placeholder by default, live Soroban contract when configured)

For the expected screen sequence, validation, and UI states behind these features, see [Main wallet user flows](docs/user-flows.md).

## Tech Stack

React Native, Expo Router, Zustand, Stellar SDK, SecureStore, AsyncStorage

## Quick Start

```bash
npm install --legacy-peer-deps
cp .env.example .env
npm start
```

Other scripts:

```bash
npm run android   # Launch on Android
npm run ios       # Launch on iOS (macOS only)
npm run web       # Launch in a browser (limited support)
npm test          # Run the Jest test suite
npm run typecheck # TypeScript type checking
npm run lint      # Lint the project
```

### Running Locally

```bash
git clone https://github.com/mondaymose/btyrewqn.git
cd btyrewqn
npm install --legacy-peer-deps
cp .env.example .env
npm start
```

## Project Structure

```
btyrewqn/
├── app/                  # Expo Router screens (file-based routing)
│   ├── (auth)/           # Auth flow: welcome, create wallet, import wallet
│   └── (tabs)/           # Main tab navigation: home, history, vault, settings
├── src/
│   ├── components/       # Reusable UI components
│   ├── constants/        # Theme tokens (colours, spacing, typography)
│   ├── features/         # Feature modules (wallet, payments, vault, contacts, ...)
│   ├── services/         # Stellar SDK integration
│   └── store/            # Zustand state stores
├── docs/                 # Guides, checklists, and design documentation
└── tests/                # Test suites and fixtures
```

## Documentation

- [Architecture Readiness Review](./docs/architecture-readiness-review.md) - Feature boundaries, duplicated state, SDK integration blockers, security-sensitive areas, and test gaps
- [Evaluation-Readiness Index](./docs/evaluation-readiness-index.md) - Central index linking all evaluation-readiness requirements, including payment expectations, tests, CI, and reviewer checklists
- [Issue Approval Readiness Checklist](./docs/issue-approval-readiness-checklist.md) - Fast pre-approval gate covering implementation completeness, tests, CI status, acceptance criteria, documentation, and known limitations
- [Evaluation Readiness Checklist](./docs/evaluation-readiness-checklist.md) - Contributor checklist for mobile issues, including tests, CI, screenshots, and acceptance criteria
- [Payment-Period Communication Policy](./docs/payment-period-communication-policy.md) - How contributors should communicate during the payment evaluation period
- [Self-Review Checklist](./docs/self-review-checklist.md) - Quick checklist to run before opening a PR
- [Contributor Self-Assessment](./docs/contributor-self-assessment.md) - Pre-review form for confirming scope, test evidence, CI, documentation, limitations, and acceptance criteria
- [Meaningful Change Threshold Guide](./docs/meaningful-change-threshold-guide.md) - What constitutes a meaningful change and how reviewers should assess PR scope and completeness
- [Reviewer Evidence Checklist](./docs/reviewer-evidence-checklist.md) - Maintainer-facing checklist for reviewing whether a PR is complete and evaluation-ready
- [Storage Guide](./docs/storage.md) - SecureStore vs AsyncStorage
- [Test-First Contribution Guide](./docs/test-first-contribution-guide.md) - Required test planning, happy-path and negative-path coverage, and local verification commands
- [Low-Effort Contribution Examples](./docs/low-effort-contribution-examples.md) - Worked examples of superficial changes and their improved alternatives
- [Contacts Guide](./docs/contacts.md) - Contact storage, backup limitations, and future export/import ideas
- [Contact Import Design](./docs/contact-import-design.md) - Design for safe contact import, validation, duplicate handling, and privacy boundaries
- [Polyfills Guide](./docs/polyfills.md) - React Native polyfills and import order for the Stellar SDK
- [Vault UI Guidance](./docs/vault-ui-guidance.md) - How to present the Soroban Savings Vault, Testnet risks, and contract limitations
- [Vault Integration Assumptions](./docs/vault-integration-assumptions.md) - Expected SDK/contract dependencies, placeholder behaviors, and known gaps
- [Vault Integration Risks](./docs/vault-integration-risks.md) - Technical integration risk analysis and cross-repo coordination roadmap
- [Vault Feature Module](./src/features/vault/README.md) - Architectural guide for components, hooks, stores, and dual-mode vault execution
- [Mobile Wallet Security FAQ](./docs/WALLET_SECURITY_FAQ.md) - Local storage, secret handling, reset behaviors, and security guarantees
- [Accessibility Checklist](./docs/accessibility.md) - Required mobile accessibility checks and reusable-component review guidance
- [UI State Catalogue](./docs/ui-states.md) - Canonical loading, empty, error, success, disabled, and pending behavior for each screen
- [Scan-to-Pay Review](./docs/scan-to-pay.md) - QR scan → validate → review screen → cancel-before-payment flow (never signs on scan)
- [Release Testing Checklist](./docs/release-testing-checklist.md) - Manual QA checklist run before every tagged build
- [Screen Inventory](docs/screen-inventory.md) - A map of the main screens and routes in the app
- [Screen Test Matrix](docs/screen-test-matrix.md) - Which test types and visual verification each screen requires
- [Mobile Onboarding Checklist](docs/mobile-onboarding-checklist.md) - Quick-reference setup checklist for new contributors
- [QR Receive Payload Format](docs/qr-payment-requests.md) - The address-only and SEP-0007-based payment-request formats the Receive screen encodes
- [Test Fixture Framework](docs/testing/fixtures.md) - Reusable, typed fixtures for wallet, payment, vault, transaction, error, and diagnostics states
- [Traceability Table Guide](docs/traceability-table.md) - How to map changes to issue acceptance criteria

## Ecosystem

`btyrewqn` builds on the wider Stellar ecosystem and the PocketPay tooling it was derived from:

- [PocketPay SDK](https://github.com/Axionvera/pocketpay-sdk)
- [PocketPay Contracts](https://github.com/Axionvera/pocketpay-contracts)

## Screenshots

> 📸 Screenshots below are placeholders. To update them, capture each screen from a simulator or device (use dummy/funded Testnet data only — never real keys or mainnet funds) and replace the files in `docs/screenshots/`.

|                    Wallet                     |                  Send                  |                     Receive                      |
| :-------------------------------------------: | :------------------------------------: | :----------------------------------------------: |
| ![Wallet screen](docs/screenshots/wallet.png) | ![Send screen](docs/screenshots/send.png) | ![Receive screen](docs/screenshots/receive.png) |
|      _Balance overview and quick actions_      |     _Send XLM to any Stellar address_  |          _QR code for your public key_           |

|                       Activity                       |                     Contacts                      |                    Vault                    |
| :--------------------------------------------------: | :-----------------------------------------------: | :-----------------------------------------: |
|  ![Activity screen](docs/screenshots/activity.png)   | ![Contacts screen](docs/screenshots/contacts.png) | ![Vault screen](docs/screenshots/vault.png) |
| _Transaction history with sent/received indicators_  |        _Saved addresses for quick access_         |       _Soroban Savings Vault (mock)_        |

### Updating screenshots

1. Run the app in a simulator with a funded Testnet account.
2. Navigate to the relevant screen.
3. Take a screenshot and export it at roughly **390 × 844 px** (iPhone 14 logical resolution) or equivalent Android size.
4. Save it to `docs/screenshots/<screen-name>.png` using the filenames shown above.
5. Commit only the image files — never include screenshots that reveal a real secret key or personal data.

## Continuous Integration (CI)

All contributions must pass the automated CI pipelines before review and merge. See the [CI Pass Requirements Guidance](docs/CI_REQUIREMENTS.md) for local reproduction commands and guidance on resolving failing checks.
