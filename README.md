# Practical 6 — Frame-by-Frame Animation & Splash (Twin/Tween) Animation

**Repository:** `MAD_24012022002_P6`
**Author:** OM KUSHWAHA
**Language:** Kotlin (Android)

---

## Project Aim

Create an Android application to demonstrate **frame-by-frame (drawable) animation** and a splash screen that demonstrates **tween (often written “twin” by mistake) animation** — i.e., simple property transformations like translate/scale/rotate/alpha. The app shows how to implement both animation techniques in an Android app. ([Android Developers][1])

> **Note:** The user text said *“twin animation”*. The standard Android term is **tween animation** (short for *in-betweening*), which interpolates properties between start and end values. If you really meant something else by “twin”, tell me and I’ll adjust the README. ([Android Developers][2])

---

## Table of Contents

* [Description](#description)
* [Features](#features)
* [Prerequisites](#prerequisites)
* [Installation & Run](#installation--run)
* [How It Works](#how-it-works)

  * [Frame-by-Frame Animation](#frame-by-frame-animation)
  * [Tween Animation (Splash Screen)](#tween-animation-splash-screen)
* [Project Structure](#project-structure)
* [Usage](#usage)
* [Testing & Notes](#testing--notes)
* [License & Author](#license--author)

---

## Description

This practical demonstrates two common Android animation approaches:

1. **Frame-by-Frame (Drawable) Animation** — playing a sequence of drawable frames to create animation (like a flipbook).
2. **Tween Animation** — applying transformations (translation, scale, rotation, alpha) to Views during the splash screen to create motion effects.

Both approaches use Android's view animation / drawable animation APIs and are implemented in Kotlin. ([Android Developers][1])

---

## Features

* Splash screen demonstrating tweened animation (translation/scale/alpha/rotate).
* A sample Activity showing frame-by-frame animation using `AnimationDrawable` or drawable animation resource.
* Clean Kotlin code and Android Studio / Gradle project setup.
* Compatible with modern Android Studio (use the provided Gradle wrapper).

---

## Prerequisites

* Android Studio (Arctic Fox or later recommended).
* JDK 11+ (use the JDK version supported by your Android Studio).
* Android SDK (install via Android Studio).
* Emulator or Android device (USB debugging enabled).

---

## Installation & Run

1. **Clone the repo**

   ```bash
   git clone https://github.com/omkushwaha9/MAD_24012022002_P6.git
   cd MAD_24012022002_P6
   ```

2. **Open in Android Studio**

   * File → Open → select project folder `MAD_24012022002_P6`
   * Let Gradle sync and download dependencies.

3. **Build & Run**

   * Run the app on an emulator or a connected device (Shift+F10 or the Run ▶ button).
   * Or from terminal (wrapper included):

     ```bash
     ./gradlew assembleDebug
     ./gradlew installDebug
     ```

   (On Windows use `gradlew.bat`.)

---

## How It Works

### Frame-by-Frame Animation

* Frame animation (Drawable animation) is implemented by supplying a sequence of drawable images (frames) and playing them using `AnimationDrawable` or a drawable XML animation-list resource.
* Typical steps:

  * Put each frame image in `res/drawable/`.
  * Create an animation-list XML (e.g., `res/drawable/my_frame_anim.xml`) listing frames and durations.
  * In code, set the drawable as `ImageView`'s background and start the `AnimationDrawable`:

    ```kotlin
    val anim = imageView.background as AnimationDrawable
    anim.start()
    ```
* Useful for sprite-like animations where each frame is an independent image. ([coursedrill.com][3])

### Tween Animation (Splash Screen)

* Tween animation creates movement/transformations by interpolating properties between start and end values — translate, rotate, scale, alpha.
* Typical usage:

  * Define tween XMLs in `res/anim/` (e.g., `res/anim/slide_in.xml`, `res/anim/zoom_in.xml`).
  * Apply with `AnimationUtils.loadAnimation(context, R.anim.your_anim)` and `view.startAnimation(anim)`.
* Usually used for splash screens, small UI effects, and view transitions. ([Android Developers][2])

---

## Project Structure (based on repo)

```
.MAD_24012022002_P6/
├─ .idea/
├─ app/
│  ├─ src/main/
│  │  ├─ AndroidManifest.xml
│  │  ├─ java/ (Kotlin code)
│  │  ├─ res/
│  │  │  ├─ drawable/        # frame images + animation-list xmls
│  │  │  ├─ anim/            # tween (splash) xmls
│  │  │  ├─ layout/          # activity / splash layouts
│  │  │  └─ values/
│  └─ build.gradle.kts
├─ gradle/
├─ gradlew
├─ gradlew.bat
├─ build.gradle.kts
└─ settings.gradle.kts
```

> The repository is Kotlin 100% as detected. (Project folders `.idea`, `app`, and Gradle scripts are present.)

---

## Usage / Screens

* **Splash Screen**: Launches with tween animations applied (logo fade/zoom/translate). After animation completes, navigates to the main Activity.
* **Main Activity**: Contains an `ImageView` or custom view demonstrating frame animation. Buttons can start/stop or change animation speed.

---

## Common Files You May Edit / Inspect

* `app/src/main/res/drawable/` — frame images & `animation-list` XML.
* `app/src/main/res/anim/` — tween XMLs for splash animation.
* `app/src/main/res/layout/activity_splash.xml` — splash layout.
* `app/src/main/java/.../SplashActivity.kt` — code to start tween and transition.
* `app/src/main/java/.../FrameAnimActivity.kt` — code controlling `AnimationDrawable`.

---

## Tips & Troubleshooting

* Make sure images for frame animation are not too large — prefer web-optimized PNGs to prevent OOM on low-end devices.
* When using `AnimationDrawable`, call `imageView.post { (imageView.background as AnimationDrawable).start() }` if starting in `onCreate()` so the view is ready.
* If animations don't show, check that the drawables and XML resources are referenced correctly and that `setBackgroundResource()` / `android:background` is used where needed.
* Use `adb logcat` to see runtime errors if the app crashes on startup.

---

## References

* Android View Animation (Tween) — Android Developers. ([Android Developers][2])
* Animation resources — Android Developers. ([Android Developers][1])

---

## License

Add your preferred license here (e.g., MIT). Example:

```
MIT License
Copyright (c) 2025 OM KUSHWAHA
```

---

## Author

OM KUSHWAHA — Student / Developer

---
