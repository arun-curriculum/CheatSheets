# Deploying Cordova Android Apps to Google Play

## Building the App

Make sure Android Home and Tools paths are set:

```
export ANDROID_HOME="/Users/<user>/Library/Android/sdk/"
export ANDROID_TOOLS="/Users/<user>/Library/Android/sdk/tools"
export ANDROID_PLATFORM_TOOLS="/Users/<user>/Library/Android/sdk/platform-tools"
```

## Building for Release

Build the Cordova project for release:

```
cordova build android --release
```

## Signing App Using Jarsigner

1. Generate a private key:

```
keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000
```

2. Sign your app with jarsigner:

```
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore my_application.apk alias_name
```

3. Verify signing:

```
jarsigner -verify -verbose -certs my_application.apk
```

4. Zipalign final APK:

```
zipalign -v 4 your_project_name-unaligned.apk your_project_name.apk
```

