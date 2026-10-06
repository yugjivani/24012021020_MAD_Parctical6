# MAD Practical-6 – Frame by Frame Animation and Splash Screen

## 📱 Frame by Frame Animation and Splash Screen with Twin Animation

### 🎯 AIM

Create an Android application to demonstrate **Frame by Frame Animation** and a **Splash Screen** using **Twin Animation**.

---

## 📌 Objectives

This practical demonstrates:

* Frame by Frame Animation
* Twin Animation
* Splash Screen
* `ImageView`
* `AnimationDrawable`
* Animation XML resources
* Scale Animation
* Translate Animation
* Rotate Animation
* Alpha Animation
* Gradient Background
* Edge-to-Edge Content Display
* Immersive Mode
* Activity Transition Animation

---

## 📚 Study

The following Android concepts are covered:

* ImageView
* Frame by Frame Animation
* Twin Animation
* Immersive Mode
* Edge-to-Edge Display
* Splash Screen
* AnimationDrawable
* `onWindowFocusChanged()`
* `AnimationUtils`
* `loadAnimation()`
* `setAnimationListener()`
* `overridePendingTransition()`
* `finish()`
* `anim` folder in `res`
* SVG to XML Drawable Conversion

---

# 🎞️ What is Frame by Frame Animation?

**Frame by Frame Animation** is an animation technique in which a sequence of images is displayed one after another.

Each image represents one frame of the animation.

```text
Frame 1 → Frame 2 → Frame 3 → Frame 4
              ↓
          Animation
```

Android provides `AnimationDrawable` to implement Frame by Frame Animation.

The frames are generally defined using the `<animation-list>` tag.

---

# 🎭 What is Twin Animation?

**Twin Animation** means applying two or more animation effects to a view.

Common Android animation types include:

* Scale
* Translate
* Rotate
* Alpha

These animations can be combined using the `<set>` tag.

Example:

```xml
<set>

    <scale />

    <translate />

    <rotate />

    <alpha />

</set>
```

---

# 🚀 Application Flow

```text
                START
                  │
                  ↓
          SplashActivity
                  │
                  ↓
        Gradient Background
                  │
                  ↓
           Twin Animation
                  │
                  ↓
        Animation Completed
                  │
                  ↓
            MainActivity
                  │
                  ↓
      Frame by Frame Animation
```

---

# 🖼️ MainActivity

`MainActivity` is the main screen of the application.

An `ImageView` is used to display images and demonstrate Frame by Frame Animation.

The animation is created using multiple drawable images.

---

# 🌈 SplashActivity

`SplashActivity` is displayed when the application starts.

It contains:

* Gradient background
* Pink and blue colors
* Twin Animation
* Activity transition animation

After the animation is completed, `MainActivity` is opened.

---

# 🎨 Splash Screen Gradient

The Splash Screen background is created using the `<gradient>` tag inside a `<shape>` drawable.

### Required Properties

| Property      | Value     |
| ------------- | --------- |
| Shape         | Rectangle |
| Gradient Type | Radial    |
| Center X      | `0.9`     |
| Center Y      | `0.9`     |
| Radius        | `1500`    |
| Start Color   | Pink      |
| End Color     | Blue      |

Example:

```xml
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">

    <gradient
        android:type="radial"
        android:centerX="0.9"
        android:centerY="0.9"
        android:gradientRadius="1500"
        android:startColor="#FFC0CB"
        android:endColor="#0000FF" />

</shape>
```

---

# 🎬 AnimationDrawable

`AnimationDrawable` is used to display multiple images sequentially.

The frames are defined using the `<animation-list>` tag.

Example:

```xml
<animation-list
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:oneshot="false">

    <item
        android:drawable="@drawable/frame1"
        android:duration="1000" />

    <item
        android:drawable="@drawable/frame2"
        android:duration="1000" />

    <item
        android:drawable="@drawable/frame3"
        android:duration="1000" />

</animation-list>
```

---

# 🔁 oneShot Attribute

The `oneShot` attribute controls whether the Frame by Frame Animation repeats.

### `android:oneshot="true"`

The animation runs only once.

### `android:oneshot="false"`

The animation repeats continuously.

Example:

```xml
android:oneshot="true"
```

---

# 🎞️ Twin Animation

Twin Animation is created using the `<set>` tag.

The practical includes:

```xml
<set>
    <scale />
    <translate />
    <rotate />
    <alpha />
</set>
```

This allows multiple animation effects to be applied to the same view.

---

# 📐 Scale Animation

Scale Animation changes the size of a view.

```xml
<scale
    android:fromXScale="0.0"
    android:toXScale="1.0"
    android:fromYScale="0.0"
    android:toYScale="1.0"
    android:duration="1000" />
```

---

# ↔️ Translate Animation

Translate Animation moves a view from one position to another.

```xml
<translate
    android:fromXDelta="0"
    android:toXDelta="0"
    android:fromYDelta="100"
    android:toYDelta="0"
    android:startOffset="100"
    android:duration="1000" />
```

Here:

```text
startOffset = 100 milliseconds
duration    = 1000 milliseconds
```

---

# 🔄 Rotate Animation

Rotate Animation rotates a view.

```xml
<rotate
    android:fromDegrees="0"
    android:toDegrees="360"
    android:duration="1000" />
```

---

# 👻 Alpha Animation

Alpha Animation changes the transparency of a view.

```xml
<alpha
    android:fromAlpha="0.0"
    android:toAlpha="1.0"
    android:duration="1000" />
```

It can be used to create fade-in and fade-out effects.

---

# ⏱️ Animation Duration

The `duration` attribute specifies how long an animation takes.

```xml
android:duration="1000"
```

`1000` milliseconds = **1 second**.

---

# ⏳ Animation Start Offset

The `startOffset` attribute specifies the delay before an animation starts.

```xml
android:startOffset="100"
```

The animation starts after **100 milliseconds**.

---

# ⚙️ AnimationUtils

`AnimationUtils` is used to load animation resources from the `res/anim` folder.

Example:

```kotlin
val animation = AnimationUtils.loadAnimation(
    this,
    R.anim.twin_animation
)
```

---

# 📥 loadAnimation()

The `loadAnimation()` method loads an XML animation resource.

Example:

```kotlin
val animation = AnimationUtils.loadAnimation(
    this,
    R.anim.twin_animation
)

imageView.startAnimation(animation)
```

---

# 👂 setAnimationListener()

`setAnimationListener()` is used to perform actions when an animation:

* Starts
* Ends
* Repeats

Example:

```kotlin
animation.setAnimationListener(
    object : Animation.AnimationListener {

        override fun onAnimationStart(
            animation: Animation?
        ) {
        }

        override fun onAnimationEnd(
            animation: Animation?
        ) {
            // Open MainActivity
        }

        override fun onAnimationRepeat(
            animation: Animation?
        ) {
        }
    }
)
```

It can be used to open `MainActivity` after the Splash Screen animation ends.

---

# 🪟 onWindowFocusChanged()

`onWindowFocusChanged()` is called when an Activity gains or loses window focus.

It can be used for full-screen and immersive UI behavior.

Example:

```kotlin
override fun onWindowFocusChanged(hasFocus: Boolean) {
    super.onWindowFocusChanged(hasFocus)

    if (hasFocus) {
        // Full screen / immersive mode
    }
}
```

---

# 📱 Edge-to-Edge Content Display

**Edge-to-edge** allows application content to extend behind system bars such as the status bar and navigation bar.

It provides a modern full-screen style UI.

```text
┌─────────────────────────────┐
│       Status Bar            │
│─────────────────────────────│
│                             │
│        App Content          │
│                             │
│        App Content          │
│                             │
│─────────────────────────────│
│      Navigation Bar         │
└─────────────────────────────┘
```

---

# 🖥️ Immersive Mode

**Immersive Mode** provides a full-screen experience by hiding or minimizing system UI such as the status bar and navigation bar.

It is useful when an application requires maximum screen space.

---

# 🔄 overridePendingTransition()

`overridePendingTransition()` is used to apply an animation while moving from one Activity to another.

Example:

```kotlin
startActivity(
    Intent(this, MainActivity::class.java)
)

overridePendingTransition(
    R.anim.slide_in,
    R.anim.slide_out
)
```

---

# ❌ finish()

`finish()` closes the current Activity.

Example:

```kotlin
startActivity(
    Intent(this, MainActivity::class.java)
)

finish()
```

After the Splash Screen opens `MainActivity`, `finish()` prevents the user from returning to the Splash Activity using the Back button.

---

# 📁 Animation Folder

Animation XML files are stored inside the `anim` folder.

```text
res/
├── anim/
│   ├── twin_animation.xml
│   ├── slide_in.xml
│   └── slide_out.xml
│
├── drawable/
│   ├── frame1.xml
│   ├── frame2.xml
│   └── splash_background.xml
│
└── layout/
    ├── activity_main.xml
    └── activity_splash.xml
```

---

# 🖼️ ImageView

`ImageView` is used to display images and drawable resources.

Example:

```xml
<ImageView
    android:id="@+id/imageView"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/frame1" />
```

In this practical, `ImageView` is used to display the Frame by Frame Animation.

---

# 🔄 SVG File to XML

SVG files can be converted into Android Vector Drawable XML files using Android Studio.

The converted drawable can be stored in:

```text
res/drawable/
```

and used in an `ImageView`.

Example:

```xml
android:src="@drawable/my_image"
```

---

# 📂 Project Structure

```text
24012021020_MAD_Parctical6/
│
├── app/
│   └── src/
│       └── main/
│           ├── java/
│           │   └── ...
│           │       ├── MainActivity.kt
│           │       └── SplashActivity.kt
│           │
│           ├── res/
│           │   ├── anim/
│           │   │   ├── twin_animation.xml
│           │   │   ├── slide_in.xml
│           │   │   └── slide_out.xml
│           │   │
│           │   ├── drawable/
│           │   │   ├── splash_background.xml
│           │   │   ├── frame1.xml
│           │   │   ├── frame2.xml
│           │   │   └── ...
│           │   │
│           │   ├── layout/
│           │   │   ├── activity_main.xml
│           │   │   └── activity_splash.xml
│           │   │
│           │   └── values/
│           │
│           └── AndroidManifest.xml
│
├── gradle/
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

---

# ▶️ How to Run

1. Clone this repository.
2. Open the project in **Android Studio**.
3. Wait for Gradle synchronization to complete.
4. Connect an Android device or start an emulator.
5. Click **Run ▶**.
6. `SplashActivity` will appear first.
7. Observe the gradient background and Twin Animation.
8. After the animation completes, `MainActivity` will open.
9. Observe the Frame by Frame Animation.

---

# 🧪 Expected Output

## Splash Screen

```text
┌───────────────────────────┐
│                           │
│     Splash Activity       │
│                           │
│     Twin Animation        │
│                           │
└───────────────────────────┘
```

The Splash Screen contains the radial pink-to-blue gradient and the required Twin Animation.

## Main Activity

```text
┌───────────────────────────┐
│                           │
│       MainActivity        │
│                           │
│      🖼️ Animation         │
│                           │
│   Frame 1 → Frame 2       │
│        → Frame 3          │
│                           │
└───────────────────────────┘
```

---

# 📚 Important Viva Questions

### 1. What is Frame by Frame Animation?

Frame by Frame Animation displays a sequence of images one after another to create a movement effect.

### 2. What is Twin Animation?

Twin Animation combines two or more animation effects such as scale, translate, rotate, and alpha.

### 3. What is AnimationDrawable?

`AnimationDrawable` is used to display a sequence of drawable resources as animation frames.

### 4. What is the use of `oneShot`?

It specifies whether the animation should run only once or repeat.

### 5. What is the use of `AnimationUtils`?

It is used to load animation resources from XML.

### 6. What is the use of `loadAnimation()`?

It loads an animation XML resource and returns an Animation object.

### 7. What is the use of `setAnimationListener()`?

It is used to perform actions when an animation starts, ends, or repeats.

### 8. What is the use of `startOffset`?

It specifies the delay before an animation starts.

### 9. What is the use of `duration`?

It specifies the time required for an animation to complete.

### 10. What is a Splash Screen?

A Splash Screen is the initial screen displayed when an application starts.

### 11. What is the use of `finish()`?

`finish()` closes the current Activity.

### 12. What is Edge-to-Edge?

Edge-to-edge allows application content to extend into the areas behind the system bars.

---

## 👨‍💻 Author

**Krish Sakariya**

**Enrollment No.:** `24012021020`

**Course:** B.Tech Information Technology

**Practical:** MAD Practical-6
#   2 4 0 1 2 0 2 1 0 2 0 _ M A D _ P a r c t i c a l 6  
 