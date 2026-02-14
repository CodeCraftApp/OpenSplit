# OpenSplit

**Free, open-source, offline-first expense splitting for everyone.**

OpenSplit is a cross-platform mobile app built with Flutter that makes it easy to split expenses with friends, roommates, travel companions, and more. It is a fully open-source alternative to Splitwise, designed to work offline and sync seamlessly when you are back online.

## Features

- **Groups and Friends** -- Create groups for trips, households, or any shared activity. Add friends and track who owes whom.
- **Flexible Split Methods** -- Equal, exact amounts, percentage, shares (ratios), and adjustments.
- **Multi-Payer Support** -- Multiple people can pay for a single expense.
- **Expense Categories** -- Categorize expenses with icons (Food, Transport, Accommodation, Entertainment, Utilities, Shopping, Health, and more).
- **Balances and Settlements** -- Per-friend and per-group balance views. Record settlements with a tap.
- **Debt Simplification** -- Minimize the number of payments in a group while keeping everyone's net balance the same.
- **Activity Feed** -- Chronological feed of all expense additions, edits, deletions, and settlements.
- **Receipt Attachments** -- Attach receipt images from camera or gallery.
- **Offline-First** -- Full CRUD operations work without network. Automatic sync on reconnection with conflict resolution.
- **Open Source** -- MIT licensed. Self-host, audit, or contribute.

### Planned Features

- Recurring expenses
- Multi-currency support with automatic conversion
- Receipt scanning with AI-powered extraction
- Charts and analytics
- Push notifications
- Data export (CSV/PDF)
- Splitwise data import
- Localization / i18n

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Flutter (iOS, Android, Web) |
| Architecture | Clean Architecture |
| State Management | flutter_bloc |
| Routing | go_router |
| Dependency Injection | get_it + injectable |
| Backend | Firebase (Auth, Firestore, Cloud Functions, Storage, Messaging) |
| Local Database | Drift (SQLite) |
| Error Handling | dartz (Either type) |

## Architecture

OpenSplit follows **Clean Architecture** with feature-based organization:

```
lib/
  core/           # Shared utilities, theme, DI, routing, error types
  features/
    auth/         # Authentication (login, register, profile)
    groups/       # Group management
    expenses/     # Expense CRUD and split calculations
    balances/     # Balance computation and debt simplification
    friends/      # Friend management
    activity/     # Activity feed
    settings/     # App preferences
    sync/         # Offline sync engine
```

Each feature contains three layers:

- **Domain** -- Entities, Use Cases, Repository Contracts (pure Dart, no dependencies)
- **Data** -- Models, Data Sources (Firebase + Drift), Repository Implementations, Sync Engine
- **Presentation** -- Blocs, Pages, Widgets

See the full [Product Requirements Document](docs/PRD.md) for detailed architecture diagrams, data models, and feature specifications.

## Getting Started

### Prerequisites

- Flutter SDK (3.9.2+)
- Firebase project (Auth, Firestore, Storage enabled)
- Dart SDK (included with Flutter)

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/YourUsername/OpenSplit.git
   cd OpenSplit
   ```

2. Install dependencies:
   ```bash
   flutter pub get
   ```

3. Configure Firebase:
   - Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
   - Enable Authentication (Email/Password, Google, Apple)
   - Enable Cloud Firestore
   - Enable Firebase Storage
   - Run `flutterfire configure` to generate `firebase_options.dart`

4. Run the app:
   ```bash
   flutter run
   ```

## Contributing

Contributions are welcome! Please read the contributing guidelines before submitting a pull request.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

Inspired by and incorporating the best ideas from:

- [Splitwise](https://www.splitwise.com/) -- The market leader in expense splitting
- [Spliit](https://github.com/spliit-app/spliit) -- Open-source Splitwise alternative
- [SplitPro](https://github.com/oss-apps/split-pro) -- Open-source Splitwise alternative
- [monetr](https://github.com/monetr/monetr) -- Open-source budgeting app
