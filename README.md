ReminderApp (Android)

A simple Android reminder app that lets you create reminders and receive notifications/alarms.


<img width="391" height="763" alt="Screenshot 2025-12-25 at 10 40 43 PM" src="https://github.com/user-attachments/assets/6ce7d338-1f84-487e-a882-5e13401484bb" />
<img width="430" height="757" alt="Screenshot 2025-12-25 at 10 41 10 PM" src="https://github.com/user-attachments/assets/8bb8f03f-0571-45a1-9f8a-0959537c655c" />
<img width="465" height="783" alt="Screenshot 2025-12-25 at 10 41 24 PM" src="https://github.com/user-attachments/assets/0935ddd9-bac6-4dcb-b9bf-2a1e19f34c25" />
<img width="424" height="755" alt="Screenshot 2025-12-25 at 10 41 47 PM" src="https://github.com/user-attachments/assets/dea72d4a-fa03-45da-8111-a485e3ba54ef" />

Requirements

Android Studio (recommended) or Gradle via terminal

Java 11

Android SDK + Platform Tools (adb)

An Android Emulator or a physical device with USB debugging enabled

Project Setup
1) Clone the repository
git clone https://github.com/Sgautam0001/ReminderApp.git
cd ReminderApp

2) Configure Android SDK path (local.properties)

Create a file named local.properties in the project root and add:

sdk.dir=/Users/shivam/Library/Android/sdk


Update the path if your SDK is located somewhere else.

3) Use Java 11

In terminal:

export JAVA_HOME=$(/usr/libexec/java_home -v 11)
export PATH="$JAVA_HOME/bin:$PATH"
java -version

Build the APK (Debug)
./gradlew clean assembleDebug


The debug APK will be generated here:

app/build/outputs/apk/debug/app-debug.apk

Install on Emulator / Device
1) Verify device/emulator is connected
adb devices

2) Install APK
adb install -r app/build/outputs/apk/debug/app-debug.apk

Start / Stop the App (ADB)
Check installed user apps
adb shell pm list packages -3

Start the app

Replace package name if needed:

adb shell monkey -p com.dataflair.reminderapp -c android.intent.category.LAUNCHER 1

Stop the app
adb shell am force-stop com.dataflair.reminderapp

Check if it is running (PID)
adb shell pidof com.dataflair.reminderapp

Run Using Android Studio

Open the project in Android Studio

Wait for Gradle sync to finish

Select an emulator/device

Click Run ▶

Notes / Troubleshooting

If you see SDK tool version warnings, update Android SDK Command-line Tools in Android Studio:

SDK Manager → SDK Tools → Android SDK Command-line Tools

If build fails due to Java version mismatch, ensure terminal/Gradle is using Java 11 (JAVA_HOME set correctly).

If package name differs, check:

app/build.gradle → applicationId

AndroidManifest.xml package/namespace (depends on project)
