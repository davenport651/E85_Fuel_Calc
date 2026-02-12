# How to Build the Fuel Calculator Android App

This directory contains a standard Android Studio project that wraps the `fuelcalc.html` file into a native Android application (APK).

## Prerequisites

To build this app, you need:

1.  **Android Studio** (Recommended)
    *   Download from: [developer.android.com/studio](https://developer.android.com/studio)
    *   This installs the necessary Android SDK, Java Development Kit (JDK), and Gradle tools.

**OR**

2.  **Command Line Tools**
    *   Java JDK (Version 11 or 17 recommended)
    *   Android Command Line Tools (`sdkmanager`)

## Building with Android Studio (Easiest)

1.  Open Android Studio.
2.  Select **Open**, and navigate to this `android_project` folder.
3.  Wait for Gradle to sync (this downloads dependencies).
4.  Connect your Android device via USB (ensure Developer Options > USB Debugging is on) OR create an Emulator.
5.  Click the green **Run** (Play) button in the toolbar.

This will build the APK and install it on your device.

## Building via Command Line (CLI)

If you just want the APK file without opening the IDE:

1.  Open your terminal or command prompt.
2.  Navigate to the `android_project` directory.
3.  Run the build command:
    *   **Linux/Mac:** `./gradlew assembleDebug`
    *   **Windows:** `gradlew.bat assembleDebug`

4.  Once the build finishes successfully, you will find the APK at:
    `android_project/app/build/outputs/apk/debug/app-debug.apk`

## Installing the APK

You can copy the `app-debug.apk` file to your Android phone and tap it to install. You may need to allow installing apps from unknown sources.

## Release Builds (For F-Droid / Play Store)

To build a signed release APK:

1.  Generate a keystore file:
    ```bash
    keytool -genkey -v -keystore my-release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias my-key-alias
    ```
2.  Configure signing in `app/build.gradle` (or use Android Studio's **Build > Generate Signed Bundle / APK** wizard).
3.  Run:
    *   `./gradlew assembleRelease`

## Updating the App

If you make changes to `fuelcalc.html` in the root directory:
1.  Copy the updated `fuelcalc.html` to `android_project/app/src/main/assets/index.html`.
2.  Rebuild the project.
