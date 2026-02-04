# react-native-check-update 🚀

A lightweight and modern solution for managing "In-App" updates on Android for React Native projects.

This library allows your users to always stay up-to-date with the latest version of your application without leaving the app, providing a seamless and professional update experience via the Google Play API.

## Features ✨

- ✅ **Lightweight & Simple**: No complex configurations.
- ✅ **Modern Version Compatible**: Supports modern React Native versions and Expo (Prebuild).
- ✅ **Update Flows**: Supports both "Flexible" and "Immediate" modes.
- ✅ **pnpm Ready**: Optimized for modern developer workflows.

## Installation 📦

```sh
pnpm add react-native-check-update
```

_Also compatible with npm and yarn._

## Usage 💻

Implementing update checks is straightforward. Here is a recommended example for your root file (`_layout.tsx` or `App.js`):

```tsx
import { useEffect } from "react";
import { checkForUpdate, UpdateFlow } from "react-native-check-update";

export default function RootLayout() {
  useEffect(() => {
    handleUpdates();
  }, []);

  const handleUpdates = async () => {
    try {
      // We attempt a FLEXIBLE update so the user
      // can continue using the app while it downloads
      await checkForUpdate(UpdateFlow.FLEXIBLE);
    } catch (e) {
      // Handle error or simply ignore in development
      console.log("Update check failed", e);
    }
  };

  // ... rest of your component
}
```

### Flow Options

- **Flexible (Recommended)**: Downloads the update in the background. The user can keep using the app.
- **Immediate**: Forces the user to update the app before they can continue using it.

---

## The Problem Solved 🛠️

This package was born as a necessary fork due to a critical compilation error in the original `react-native-in-app-updates` library (and similar ones) when used with modern React Native versions or with the New Architecture enabled.

### Fixed Error:

If you have encountered the following failure when building for Android:
`e: .../InAppUpdatesModule.kt:30:24 Unresolved reference 'currentActivity'`

Or a similar error related to `ActivityEventListener`, **this package is the solution**. We have corrected the native Kotlin implementation to use `getCurrentActivity()` properly, ensuring compatibility with the current React Native lifecycle.

---

## Credits and Reference

This project is a maintained and fixed fork of [react-native-in-app-updates](https://github.com/aravind3566/react-native-in-app-updates). We thank the original author for the codebase.
