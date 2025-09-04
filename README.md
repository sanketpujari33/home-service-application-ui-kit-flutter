# Moto – Home Services UI Kit (Flutter)

Moto is a modern, Material 3-based Flutter UI kit for home services apps (inspired by platforms like آچاره). It ships with polished screens, navigation, reusable widgets, and demo data to let you prototype quickly or use as a foundation for production.

## ✨ Highlights

- Material 3 design with a clean, responsive layout
- Typed models with demo data for services, reviews, and categories
- Robust navigation using `go_router` with a bottom navigation shell
- Image loading helper with graceful placeholders and web/desktop safety
- Modular feature folders and reusable UI components

## 🧰 Tech Stack

- Flutter SDK: 3.9+
- Routing: `go_router`
- UI: Material 3, custom `AppTheme`, `AppTextStyles`, `AppColors`
- Images: `ImageHelper` (safe network image loader)
- Ratings: `flutter_rating_bar`
- State: Simple local state + demo data (Provider wired for expansion)

## 🗺️ Navigation Map

Shell (bottom tabs via `MainScreen`):
- `/` → Home
- `/bookings` → Bookings
- `/profile` → Profile

Top-level routes:
- `/categories/:categoryId` → Service Category
- `/services/:serviceId` → Service Details
- `/services/:serviceId/reviews` → Service Reviews
- `/providers/:providerId` → Service Provider
- `/booking/:serviceId` → Booking flow
- `/booking-success` → Booking success
- `/notifications` → Notifications
- `/settings` → Settings
- `/addresses` → Address Management
- `/login`, `/register` → Auth (stubs)

You can find routes in `lib/core/router/app_router.dart`.

## 🧱 Project Structure

```
lib/
	core/
		models/              # Service, Review, Category, etc. with demo data
		router/              # go_router configuration
		theme/               # Colors, text styles, app theme
		utils/               # ImageHelper, helpers
		widgets/             # Reusable UI components (buttons, inputs, etc.)
	features/
		home/                # Home and featured/popular lists
		service_category/    # Category listing + sorting
		service_details/     # Details + carousel + provider + reviews snippet
		service_reviews/     # Full reviews screen with filters/tabs
		service_provider/    # Provider profile, stats, services tabs
		booking/             # Booking screens and success
		notifications/       # Notifications list
		profile/             # Profile + links to settings, addresses
		settings/            # App settings (toggles, selections)
		address/             # Address management
```

## 🚀 Getting Started

Prerequisites:
- Flutter 3.9+ installed
- Xcode (iOS) / Android Studio (Android) set up

Install dependencies:

```bash
flutter pub get
```

Run on a device or simulator:

```bash
# iOS
flutter run -d ios

# Android
flutter run -d android

# Web
flutter run -d chrome
```

Run tests:

```bash
flutter test
```

## 🖼️ Images and Caching

We use a custom `ImageHelper` wrapper for network images that:
- Provides consistent placeholders and error states
- Avoids `MissingPluginException` on platforms where `path_provider` isn’t supported
- Keeps UI stable for web and desktop

If you previously used `cached_network_image` and hit plugin init issues on iOS/web, `ImageHelper` is the safe default. Update any direct `CachedNetworkImage` usage to `ImageHelper.loadNetworkImage(...)`.

## ⚙️ iOS/Pods Notes

The project includes CocoaPods files. If you open iOS for the first time or after dependency changes:

```bash
cd ios
pod install
cd ..
```

Then build from Flutter as usual.

## 🧩 Key Screens

- Home: featured and popular services
- Service Details: image carousel, description, features, provider card, reviews preview, Book Now CTA
- Reviews: tabbed filters and rating summary
- Provider: header image, profile, verification badge, stats, services
- Category: filtering, sorting
- Profile: settings, address management, and more
- Booking: booking flow + success screen

## 🔧 Troubleshooting

- MissingPluginException for `path_provider`
	- We initialize `WidgetsFlutterBinding.ensureInitialized()` and guard `getTemporaryDirectory()` behind `!kIsWeb` in `lib/main.dart`.
	- If you add new plugins requiring platform setup, run `flutter clean` then rebuild.

- iOS build issues with Pods
	- Ensure CocoaPods is installed and run `pod install` in `ios/`.
	- Open the generated workspace if building from Xcode: `Runner.xcworkspace`.

## 📝 Contributing

Contributions are welcome! Suggested steps:
- Keep changes scoped and focused (one feature/fix per PR)
- Follow the existing folder structure and code style
- Add small screenshots/GIFs to PRs for UI changes when helpful

## 📄 License

This project is provided as-is under the MIT License. See `LICENSE` if present or include one before distribution.

