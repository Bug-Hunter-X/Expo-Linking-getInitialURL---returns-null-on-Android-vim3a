# Expo Linking.getInitialURL() Returns Null on Android

This repository demonstrates a bug where `Linking.getInitialURL()` in Expo returns `null` on Android devices even when a deep link has been successfully opened. This problem makes it challenging to handle deep links correctly upon application startup.

## Problem Description

The `Linking.getInitialURL()` method is intended to retrieve the URL that launched the application. However, in certain circumstances on Android (this bug is less frequent on iOS), it may unexpectedly return `null`, even if the app was launched through a valid deep link. The inconsistency of this issue makes it difficult to reproduce consistently.

## Reproduction Steps

1.  Clone this repository.
2.  Run the app on an Android emulator or device.
3.  Open a deep link URL (e.g. `myapp://link`).
4. Observe the console output. `Linking.getInitialURL()` might return `null` unexpectedly.

## Solution

The provided solution implements a retry mechanism with a timeout. The solution also uses `Linking.addEventListener` to handle deep links opened after the application has already started.