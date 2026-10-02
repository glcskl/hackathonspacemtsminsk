# hackathonspacemtsminsk — Android application

An Android application built for the MTS hackathon on 18 to 20 March 2025, from a technical specification provided by MTS. The application communicates with connected hardware over the network, so it uses both an HTTP client and an MQTT client.

The application lives in the `MTSHackaton-master/` directory. The root of the repository only carries this file.

## Features

- Network communication with a backend over HTTP
- MQTT messaging for live device data and events
- List-based data presentation with RecyclerView
- JSON serialisation for payloads
- Several screens built as standard Android activities
- XML layouts with Material Design components

## Tech stack

| Layer | Technology |
| --- | --- |
| Platform | Android |
| Language | Java |
| Architecture | Activities with XML layouts |
| Networking | OkHttp 4.9.1 |
| Messaging | Eclipse Paho MQTT client |
| Lists | AndroidX RecyclerView 1.2.1 |
| Serialisation | Gson 2.8.8 |
| Build tooling | Gradle |
| Package | `ry.tech.mts_hackaton` |

## Getting started

### Requirements

- Android Studio, with the Android SDK installed
- JDK 11 or newer
- A device or emulator running Android 7.0 or later
- Backend and broker endpoints, if you want live data rather than local behaviour

### Environment variables

None at build time. Endpoints and credentials are configured inside the application.

### Installation

```bash
git clone https://github.com/glcskl/hackathonspacemtsminsk.git
cd hackathonspacemtsminsk/MTSHackaton-master
```

Open the directory in Android Studio and let it resolve the Gradle dependencies, or build from the command line:

```bash
./gradlew assembleDebug
```

The debug APK is written to `app/build/outputs/apk/debug/`.

### Running

Start an emulator or connect a device with USB debugging enabled, then run:

```bash
./gradlew installDebug
```

Or launch directly:

```bash
adb shell am start -n ry.tech.mts_hackaton/.MainActivity
```

## Project structure

```
MTSHackaton-master/
  app/
    build.gradle     application module
    src/main/
      java/ry/tech/mts_hackaton/   application code
      res/layout/                  XML layouts
      res/menu/                    menu resources
      res/mipmap/                  launcher icons
  build.gradle       root build configuration
  settings.gradle    module list
  gradle.properties  Gradle settings
```

## SDK versions

| Setting | Value |
| --- | --- |
| `compileSdk` | 35 |
| `targetSdk` | 34 |
| `minSdk` | 24 |
| Source and target compatibility | Java 11 |

## Notes

This is a hackathon project produced under a two-day deadline. It has no authentication layer and stores credentials in the application, so it is not suitable for production use.