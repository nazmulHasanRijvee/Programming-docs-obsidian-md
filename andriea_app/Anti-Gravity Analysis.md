Here is an overview of the **Mercy** Flutter application architecture and project setup:

---
### 1. Technology Stack & Key Dependencies

* **Framework**: Flutter (Dart SDK `^3.11.5`)
* **State Management**: **Riverpod** ([`flutter_riverpod ^3.3.1`](file:///c:/flutter_my_projects/work_projects/andreia250472_mercy/pubspec.yaml#L40)) with `ProviderScope` at root.
* **Routing**: **GoRouter** ([`go_router ^17.2.2`](file:///c:/flutter_my_projects/work_projects/andreia250472_mercy/pubspec.yaml#L41)) with tab support via `StatefulShellRoute.indexedStack`.
* **Networking**: **Dio** + **Retrofit** with `TokenManager` interceptor for Bearer token auth & auto 401 refresh.
* **Screen Responsiveness**: **Flutter ScreenUtil** ([`flutter_screenutil ^5.9.3`](file:///c:/flutter_my_projects/work_projects/andreia250472_mercy/pubspec.yaml#L37)), configured for design size `375 x 812` (iPhone X baseline). Use `.w`, `.h`, `.r`, `.sp` extensions.
* **Local Persistence**: **SharedPreferences** wrapped in `CacheService` interface.
* **Asset & Code Generation**: **FlutterGen** ([`lib/core/gen/`](file:///c:/flutter_my_projects/work_projects/andreia250472_mercy/lib/core/gen/)), `json_serializable`, and `retrofit_generator`.

---

### 2. Architecture & Directory Structure

The project uses a **Feature-First + Core Infrastructure Layering**:

```
lib/
├── main.dart             # App entrypoint, ScreenUtil & Riverpod initialization
├── core/                 # Shared application infrastructure & global state
│   ├── const/            # Global constants & image/icon path definitions
│   ├── gen/              # Generated assets (Assets.gen.dart) & l10n
│   ├── providers/        # Top-level Riverpod providers (one provider per file)
│   ├── routes/           # GoRouter route definitions and tab navigation config
│   ├── service/          # API services (Dio/Retrofit) and local storage (CacheService)
│   └── static/           # Styling tokens, custom ThemeExtension setup, & color system
└── src/
    ├── feature/          # Feature-based modular code
    │   └── <feature_name>/presentation/<screen_name>/view/
    └── widgets/          # Shared reusable UI widgets across features
```

---

### 3. Application Initialization ([main.dart](file:///c:/flutter_my_projects/work_projects/andreia250472_mercy/lib/main.dart))

1. **Async Setup**: Initializes `WidgetsFlutterBinding` and `ScreenUtil`.
2. **System UI & Orientation**: Standardizes edge-to-edge transparent system bars and locks orientation to `portraitUp`.
3. **Dependency Injection**: Pre-fetches `SharedPreferences` and overrides `sharedPreferencesProvider` at the root `ProviderScope` level before `runApp`.
4. **App Root**: `MyApp` reads `routerProvider` from Riverpod and wraps the application with `ScreenUtilInit` and `MaterialApp.router`.

---

### 4. Key Development Commands

| Command | Purpose |
| :--- | :--- |
| `flutter analyze` | Linting & static type checking |
| `dart run build_runner build --delete-conflicting-outputs` | Regenerates Retrofit APIs, JSON serializers, and assets |
| `dart run flutter_gen_runner` | Regenerates asset definitions under [`lib/core/gen/`](file:///c:/flutter_my_projects/work_projects/andreia250472_mercy/lib/core/gen/) |
| `flutter test` | Executes widget and unit test suites |
