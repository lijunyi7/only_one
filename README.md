# OnlyOne

**OnlyOne** is a productivity app designed for ADHD and procrastination. It helps you focus on one important task at a time with smart supervision and gentle reminders.

## Features

- **Single task focus** — Add one important task and commit to it. No overwhelming lists.
- **Supervision mode**
  - **In app**: Gentle reminders every 15 seconds to keep you on track
  - **Background**: Customizable check-in interval (1 second–60 minutes) when the app is in the background
  - **Extended absence**: Extra check-in after 10 minutes if you’re still away
  - **Completion**: Reminder at the end of the focus session to confirm if you finished
- **Progress tracking** — Visual progress and focus timer
- **Statistics** — View your focus history and completion stats
- **Localization** — English and 简体中文
- **Clean UI** — Modern interface with Lottie animations and Google Fonts

## Screenshots

*
![IMG_3006](https://github.com/user-attachments/assets/31ed1983-3ab9-41cd-83ac-1458f7f4a159)
![IMG_3005](https://github.com/user-attachments/assets/77392bcc-b656-4fb6-abc3-5983a1dc8636)
![IMG_3004](https://github.com/user-attachments/assets/32afb41e-5975-447c-9f17-ca8221658352)
![IMG_3003](https://github.com/user-attachments/assets/1eec9974-cd36-479a-a103-a8e5604ff9b3)
![IMG_3007](https://github.com/user-attachments/assets/352d58f7-e3e2-4ade-b587-dd70355e426d)
*


## Getting started

### Prerequisites

- [Flutter SDK](https://flutter.dev/docs/get-started/install) (stable, SDK ^3.8.1)
- iOS 12.0+ or Android 5.0+ (API 21+)

### Install and run

```bash
git clone https://github.com/yourusername/only_one.git
cd only_one
flutter pub get
flutter run
```

### Build for release

**iOS**

```bash
flutter build ios
```

**Android**

```bash
flutter build apk
```

## Permissions

### Notifications (required)

- **iOS**: On first launch the app requests notification permission. If reminders don’t appear, enable them in **Settings → [App name] → Notifications** (Allow Notifications, Sounds, Banners).
- **Android**: Notification and “schedule exact alarm” (for reliable reminders) are requested at startup.

### Customizing reminder intervals

In **Settings** (bottom navigation):

- **Focus duration** — Length of your focus session
- **Background reminder interval** — How often you’re reminded when the app is in the background (e.g. 1–30 seconds for strict supervision, 1–5 minutes for a balanced approach, or 5–60 minutes for lighter reminders)

## Notifications behavior

| Situation              | Behavior |
|------------------------|----------|
| Using the app          | Reminder every 15 seconds |
| App in background      | Check-ins at your chosen interval |
| Return to app quickly  | Pending check-in notifications are cancelled |
| Away for 10+ minutes   | Additional 10-minute check-in |
| End of focus session   | Final notification: “Did you complete the task?” |

### If notifications don’t work (iOS)

1. **Settings → [App name] → Notifications** — Allow Notifications, Sounds, Banners.
2. **Focus / Do Not Disturb** — Ensure the app is allowed in **Settings → Focus** (or Do Not Disturb) if you use those modes.
3. Use the **Test notification** option in the app (e.g. in debug or settings) to verify.

## Project structure

```
lib/
├── main.dart                    # App entry, permissions, theme
├── l10n/                        # Localizations (en, zh)
│   ├── app_localizations.dart
│   ├── app_localizations_en.dart
│   └── app_localizations_zh.dart
├── models/
│   ├── task.dart                # Task model
│   └── app_settings.dart        # Settings model
├── providers/
│   ├── task_provider.dart       # Task and focus state
│   └── language_provider.dart   # App language
├── screens/
│   ├── main_navigation.dart     # Bottom nav shell
│   ├── home_screen.dart         # Main focus screen
│   ├── add_task_screen.dart     # Add/edit task
│   ├── task_completion_screen.dart
│   ├── settings_screen.dart     # Duration, reminders, language
│   ├── stats_screen.dart        # Focus history & stats
│   ├── help_screen.dart         # Help content
│   └── splash_screen.dart       # Launch screen
├── services/
│   └── notification_service.dart  # Scheduling, foreground/background logic
└── widgets/
    ├── focus_timer.dart         # Timer UI
    ├── task_card.dart           # Task display
    └── empty_state.dart         # Empty state UI
```

## Tech stack

- **Flutter** — UI and cross-platform
- **Provider** — State management
- **shared_preferences** — Local persistence
- **flutter_local_notifications** + **timezone** — Scheduled reminders
- **permission_handler** — Notifications and exact alarm (Android)
- **intl** + **flutter_localizations** — Dates and i18n
- **google_fonts**, **lottie**, **flutter_svg** — Typography and assets

## Contributing

1. Fork the repo
2. Create a feature branch
3. Make your changes and add tests if applicable
4. Open a pull request

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
