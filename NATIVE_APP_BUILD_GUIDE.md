# Distortion Entertainment - Native App Build Guide

This guide will help you build and publish the Distortion Entertainment app to Google Play Store and Apple App Store.

## 📱 Project Structure

```
distortion-native-app/
├── android/
│   ├── app/
│   │   ├── build.gradle
│   │   ├── src/
│   │   │   ├── main/
│   │   │   │   ├── AndroidManifest.xml
│   │   │   │   ├── java/com/distortion/entertainment/
│   │   │   │   │   └── MainActivity.kt
│   │   │   │   └── res/
│   │   │   │       ├── drawable/
│   │   │   │       ├── layout/
│   │   │   │       ├── values/
│   │   │   │       └── mipmap/
│   │   └── proguard-rules.pro
│   ├── gradle/
│   └── settings.gradle
├── ios/
│   ├── Distortion/
│   │   ├── AppDelegate.swift
│   │   ├── SceneDelegate.swift
│   │   ├── ViewController.swift
│   │   └── Assets.xcassets/
│   ├── Distortion.xcodeproj/
│   └── Podfile
├── web/
│   └── (PWA version - app.html, manifest.json, sw.js)
└── README.md
```

---

## 🚀 Quick Start

### Prerequisites
- **Android**: Android Studio, JDK 11+, NDK
- **iOS**: Xcode 12+, CocoaPods, Mac with macOS 11+
- **General**: Git, Node.js (for web version)

---

## 📦 Android Build (Google Play Store)

### Step 1: Create Android Project

```bash
# Create Android project structure
mkdir -p android/app/src/main/java/com/distortion/entertainment
mkdir -p android/app/src/main/res/drawable
mkdir -p android/app/src/main/res/layout
mkdir -p android/app/src/main/res/values
mkdir -p android/app/src/main/res/mipmap
```

### Step 2: Configure build.gradle

See `android/app/build.gradle` file in this repository.

### Step 3: Create AndroidManifest.xml

See `android/app/src/main/AndroidManifest.xml`

### Step 4: Build & Sign APK

```bash
cd android
./gradlew clean build
./gradlew bundleRelease
```

### Step 5: Upload to Google Play Store

1. Go to [Google Play Console](https://play.google.com/console)
2. Create new app
3. Fill in app details
4. Upload AAB (Android App Bundle) file
5. Submit for review

**Store Listing Details:**
- **App Name**: Distortion Entertainment
- **Category**: Business
- **Description**: Creative Excellence & Digital Innovation - Professional Graphic Design, DJ Services, Photography, Web Development, Branding & Cyber Security solutions.
- **Short Description**: Professional creative services & digital solutions
- **Target Audience**: Business, Event Planners, Entrepreneurs

---

## 🍎 iOS Build (Apple App Store)

### Step 1: Create iOS Project

Using Xcode or command line:

```bash
# Create iOS project
xcode-select --install
```

### Step 2: Open Xcode Project

```bash
cd ios
open Distortion.xcodeproj
```

### Step 3: Configure Project Settings

- **Product Name**: Distortion Entertainment
- **Organization**: Distortion Entertainment
- **Bundle Identifier**: `com.distortion.entertainment`
- **Deployment Target**: iOS 13.0+

### Step 4: Add App Icons

Place 1024x1024 icon in `ios/Distortion/Assets.xcassets/AppIcon.appiconset/`

### Step 5: Build for Distribution

```bash
# Archive app
xcodebuild archive \
  -scheme Distortion \
  -configuration Release \
  -archivePath ./Distortion.xcarchive

# Export for distribution
xcodebuild -exportArchive \
  -archivePath ./Distortion.xcarchive \
  -exportOptionsPlist ./ExportOptions.plist \
  -exportPath ./
```

### Step 6: Upload to App Store

1. Go to [App Store Connect](https://appstoreconnect.apple.com)
2. Create new app
3. Fill in app details
4. Upload build
5. Submit for review

**App Store Listing Details:**
- **App Name**: Distortion Entertainment
- **Category**: Business
- **Description**: Creative Excellence & Digital Innovation - Book professional graphic design, DJ services, photography, web development, branding, and cyber security solutions directly from your mobile device.
- **Keywords**: DJ, design, photography, branding, web development, events
- **Support URL**: https://djzeks.github.io/distortion/
- **Privacy Policy**: https://djzeks.github.io/distortion/privacy.html

---

## 📋 App Store Submission Checklist

### Google Play Store
- [ ] Create developer account ($25 one-time fee)
- [ ] Prepare 512x512 app icon
- [ ] Prepare 2-8 screenshots (1080x1920)
- [ ] Prepare feature graphic (1024x500)
- [ ] Write app description
- [ ] Set content rating
- [ ] Build and sign APK/AAB
- [ ] Upload to Play Console
- [ ] Submit for review (24-48 hours)

### Apple App Store
- [ ] Create Apple Developer account ($99/year)
- [ ] Prepare 1024x1024 app icon
- [ ] Prepare 2-5 screenshots per device size
- [ ] Prepare app preview video (optional)
- [ ] Write app description
- [ ] Set content rating
- [ ] Build and archive app
- [ ] Upload to App Store Connect
- [ ] Submit for review (1-3 days)

---

## 🔐 Signing Keys & Certificates

### Android Keystore
```bash
# Generate signing key
keytool -genkey -v -keystore distortion.jks \
  -keyalg RSA -keysize 2048 -validity 10000 \
  -alias distortion-key

# Configure in build.gradle:
signingConfigs {
    release {
        storeFile file("distortion.jks")
        storePassword "your-password"
        keyAlias "distortion-key"
        keyPassword "your-password"
    }
}
```

### iOS Certificates
- Create in Apple Developer account
- Download and install in Keychain
- Configure in Xcode: Signing & Capabilities

---

## 📱 Features in Native App

✅ **Cross-Platform WebView**
- Loads PWA from: `https://djzeks.github.io/distortion/app.html`
- Native app shell with WebView
- Works online and offline with cached content

✅ **Native Integrations**
- Direct WhatsApp messaging
- Direct phone calling
- Email integration
- Calendar integration for bookings
- Photo gallery access
- Camera integration for consultations

✅ **App Store Benefits**
- Appears in app store search
- Push notifications
- Background services
- Better performance
- Native look and feel

---

## 🔄 Update Process

Once published:

1. **Web Updates**: Simply update `https://djzeks.github.io/distortion/app.html`
2. **App Store Updates**: Follow submission process for major changes
3. **Automatic Updates**: Users get new version from app stores

---

## 💰 Costs

| Service | Cost | Frequency |
|---------|------|-----------|
| Google Play Store | $25 | One-time |
| Apple Developer Program | $99 | Yearly |
| Testing Devices | Variable | One-time |
| **Total First Year** | **~$100-150** | - |

---

## 📊 App Store SEO

### Keywords for Google Play
- Distortion Entertainment
- DJ services Kenya
- Graphic design app
- Photography booking
- Event planning
- Creative services
- Web development
- Branding services

### Keywords for Apple App Store
- Distortion Entertainment
- DJ Booking
- Event Services
- Creative Design
- Photography Services
- Branding Platform
- Professional Services

---

## 🆘 Support & Resources

- **Android Development**: [Android Developer Docs](https://developer.android.com/)
- **iOS Development**: [Apple Developer Docs](https://developer.apple.com/documentation/)
- **Google Play Console**: [play.google.com/console](https://play.google.com/console)
- **App Store Connect**: [appstoreconnect.apple.com](https://appstoreconnect.apple.com)

---

## 📞 Contact

For questions about the app:
- **WhatsApp**: +254 742 438 180
- **Email**: contact@distortion.com
- **Website**: https://djzeks.github.io/distortion/

---

## 📜 Version History

- **v1.0** - Initial native app release
- Supports Android 8.0+ and iOS 13.0+
- Integrated PWA WebView
- Native app store listing

**Made with ❤️ by Distortion Entertainment**
