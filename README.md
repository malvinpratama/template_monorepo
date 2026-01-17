# Flutter Monorepo Template

A well-structured Flutter monorepo template built with Melos for managing multiple packages and apps as Git submodules. This template provides a solid foundation for scalable Flutter applications with clean architecture principles.

## 🏗️ Project Structure

```
template_monorepo/
├── apps/                           # Flutter application (Git submodule)
│   ├── lib/                        # Main app code
│   ├── android/                    # Android platform files
│   ├── ios/                        # iOS platform files
│   ├── web/                        # Web platform files
│   ├── windows/                    # Windows platform files
│   ├── macos/                      # macOS platform files
│   ├── linux/                     # Linux platform files
│   └── pubspec.yaml               # App dependencies
├── packages/                       # Reusable packages (Git submodules)
│   ├── core/                      # Core services
│   │   ├── database_service/      # Database management
│   │   ├── di_service/           # Dependency injection
│   │   ├── logger_service/       # Logging utilities
│   │   ├── route_service/        # Navigation & routing
│   │   └── theme_service/        # Theme management
│   ├── modules/                   # Feature modules (empty)
│   ├── repositories/              # Data repositories (empty)
│   └── utilities/                 # Utility packages
│       ├── encrypt_utils/         # Encryption utilities
│       └── shared/               # Shared utilities & configurations
└── pubspec.yaml                  # Workspace configuration
```

## 🚀 Features

- **Monorepo Management**: Powered by [Melos](https://melos.invertase.dev/) for efficient package management
- **Git Submodules**: Each package and app is managed as separate Git repositories
- **Clean Architecture**: Separation of concerns with core services and utilities
- **Dependency Injection**: Built-in DI service using GetIt and Injectable
- **State Management**: Flutter BLoC pattern with Talker logging integration
- **Navigation**: Go Router for type-safe navigation
- **Database**: Database service layer with SharedPreferences
- **Theme Management**: Centralized theme service with Google Fonts support
- **Build Tools**: Automated code generation with build_runner, freezed, json_serializable
- **Multiple Environments**: Environment configuration with dart-define support
- **Custom Icons**: Flutter launcher icons with staging/production variants
- **Multi-platform**: Support for Android, iOS, Web, Windows, macOS, and Linux
- **Firebase Integration**: Firebase Analytics and Crashlytics support
- **Package Rename**: Support for app renaming for different environments

## 📋 Prerequisites

Before getting started, ensure you have the following installed:

- [Flutter SDK](https://docs.flutter.dev/get-started/install) (>=3.9.2)
- [Dart SDK](https://dart.dev/get-dart) (>=3.9.2)
- [Melos](https://melos.invertase.dev/getting-started) (>=7.3.0)

Install Melos globally:
```bash
dart pub global activate melos
```

## 🏁 Getting Started

### 1. Clone and Setup

```bash
# Clone the repository with submodules
git clone --recurse-submodules <repository-url>
cd template_monorepo

# If already cloned, initialize submodules
git submodule update --init --recursive

# Bootstrap the monorepo (installs dependencies for all packages)
melos bootstrap
```

### 2. Get All Packages

```bash
# Get dependencies for all packages
melos run get:packages
```

### 3. Generate Code

```bash
# Generate code for packages (build_runner, json_serializable, etc.)
melos run gen:packages
```

### 4. Run the App

```bash
cd apps
flutter run
```

## 🛠️ Available Commands

This monorepo includes several Melos scripts to streamline development:

### Development Commands

```bash
# Install dependencies for all packages
melos run get:packages

# Generate code (build_runner, json_serializable, freezed, etc.)
melos run gen:packages

# Analyze code across all packages
melos run analyze
```

### Environment Setup

```bash
# Setup staging environment
melos run rename:staging

# Setup production environment  
melos run rename:production

# Generate launcher icons for staging
melos run launcher:staging

# Generate launcher icons for production
melos run launcher:production
```

### Build Commands

```bash
# Build APK with environment variables
flutter build apk --release --dart-define=flavor=staging --dart-define=appName="App Staging" --dart-define=baseUrl="https://staging.api.com"

# Clean build runner cache
dart run build_runner clean
```

## 🎯 Core Packages

### Database Service
Abstract database service layer for data persistence operations.

### DI Service  
Dependency injection orchestrator that works with GetIt and Injectable for managing service initialization.

### Logger Service
Centralized logging utilities for debugging and monitoring.

### Route Service
Navigation and routing service using Go Router with dependency injection support.

### Theme Service
Centralized theme management service with database integration for persistent theme settings.

### Encrypt Utils
Security utilities package for data encryption and decryption operations.

### Shared
Common utilities, configurations, and external dependencies including:
- Environment configuration (Env class)
- Firebase integration (Analytics, Crashlytics)
- Talker logging (Flutter, BLoC, Dio loggers)
- State management utilities
- Shared preferences and Google Fonts

## 📱 Multi-Platform Support

This template supports all Flutter platforms:

- **Mobile**: Android, iOS
- **Desktop**: Windows, macOS, Linux  
- **Web**: Progressive Web App ready

## 🔧 Configuration

### Environment Configuration

The template supports multiple environments using dart-define:

```bash
# Available environment variables
--dart-define=flavor=staging|production
--dart-define=appName="Your App Name"
--dart-define=baseUrl="https://api.example.com"
```

Environment values are handled by the `Env` class in the shared package:

```dart
class Env {
  final String flavor;
  final String appName;
  final String baseUrl;
}
```

### Git Submodules

Each package and the main app are managed as separate Git repositories:

```bash
# Update all submodules
git submodule update --remote

# Add new submodule
git submodule add -b develop https://github.com/username/package.git packages/new_package
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📚 Additional Resources

- [Flutter Documentation](https://docs.flutter.dev/)
- [Melos Documentation](https://melos.invertase.dev/)
- [Flutter BLoC Documentation](https://bloclibrary.dev/)
- [Go Router Documentation](https://docs.page/csells/go_router)
- [GetIt Documentation](https://pub.dev/packages/get_it)
