# Feature Manager

Override Android system features **per app** to switch application variants: PC / ChromeOS, TV / Leanback, tablet, phone, or automotive. Built on [libxposed API 102](https://github.com/JingMatrix/libxposed-api).

Package name: `io.github.indusy55.featuremanager`

## Download

Latest release: https://github.com/indusy55/io.github.indusy55.featuremanager/releases

## Source

MIT licensed, source code: https://github.com/indusy55/io.github.indusy55.featuremanager

## Features

- Tri-state rules for any `PackageManager` feature: default, force-enable, or force-disable.
- Hooks `hasSystemFeature(String)`, `hasSystemFeature(String, int)` and `getSystemAvailableFeatures()` in `android.app.ApplicationPackageManager`.
- Built-in patch-style templates: PC (Desktop / ARC / ChromeOS), TV (Leanback), tablet, phone, automotive.
- Per-app scope status and "rules loaded" indication.
- Local-only configuration; no network access, ads, analytics, or personal data collection.

## Usage

1. Install the APK and enable the module in your Xposed manager.
2. Add the target apps to the module scope. The baseline scope contains only the module itself; other apps can be added from the module UI or the framework manager.
3. Open Feature Manager, then either configure individual features under **Apps**, or apply a template under **Templates** (applying a template = patch).
4. Force-stop and reopen the target app. When the target process loads the rules, the home screen shows **已生效** ("loaded").

A common example is making Google Play serve the **Desktop** build of Chrome Canary: apply the complete PC template (including `com.google.desktop.gms`), not just `android.hardware.type.pc`.

## Requirements

An Xposed framework implementing libxposed API 102. Use at your own risk: spoofing system features may break apps or violate third-party service terms.
