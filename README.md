# Hisaab for Android

A money tracker for your online payments and your cash. Written in Kotlin with Jetpack Compose, stored in a local Room database.

Everything stays on the phone. The app has no internet permission.

## Run it on your phone

1. Install Android Studio (Koala or newer) on your computer.
2. In Android Studio choose File > Open and pick this `hisaab-android` folder. Let Gradle sync finish. It downloads what it needs, so the first sync takes a few minutes.
3. On your phone open Settings > About phone, tap Build number seven times, then turn on Developer options > USB debugging.
4. Connect the phone with a USB cable and accept the "Allow USB debugging" prompt.
5. Pick your phone in the device list at the top of Android Studio and press Run.

To get an APK to share instead, use Build > Build Bundle(s) / APK(s) > Build APK(s).

## Try auto-tracking

- Open the app, tap the sliders icon on Home, and switch on Bank SMS alerts. Android asks for SMS permission. Hisaab then scans the last 60 days and listens for new messages.
- No bank SMS handy? In the Android emulator open Extended controls > Phone and send a text such as:
  `Rs.412.00 debited from A/c XX1234 on 12-11-26 to VPA swiggy@icici (UPI Ref 123456)`
- UPI app notifications: switch it on, then allow Hisaab in the notification access screen that opens.

## What is here

- Home, Add expense (cash or online, new categories), Activity (search, filters, long-press to delete), Insights, Auto-tracking.
- `capture/SmsParser.kt` reads bank messages. Banks word their SMS differently, so when one is missed, add its pattern there and a case to `SmsParserTest`.
- A payment that arrives as both an SMS and a UPI app notification is saved once.

## Not built yet

- Email receipts. Reading Gmail needs a Google sign-in set up in Google Cloud and an internet permission, so the switch is shown but disabled.
- Scanning paper bills, and picking a date other than now.
- Budgets per category. The monthly budget is fixed at Rs 45,000 in `Prefs.kt`.

## Good to know

- This was written without being compiled, so expect to fix a few small errors on the first build.
- Google Play restricts apps that ask for SMS permission. Installing it yourself is fine, but a Play Store release needs a separate approval.
