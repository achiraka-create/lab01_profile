Lab L1 – About me
Course: COE67-332
Name: Achira Kansuwan
Student ID: 67111823
Repository: https://github.com/achiraka-create/lab01_profile

Q1 – Tools
When I ran flutter doctor, Flutter and Android toolchain passed, but Visual Studio was not installed. I did not need to install it because this lab uses an Android emulator, not Windows desktop.

I also encountered an ADB unauthorized error when connecting to the emulator. I used adb devices to check the connection, revoked the USB debugging authorizations in Developer options, and turned USB debugging off and on again. After allowing the connection, the emulator status changed to device.

During the first build, Android NDK 28.2.13676358 was missing, so I installed it through Android Studio SDK Manager. I also encountered a Gradle VerifyException. I added -Duser.language=en -Duser.country=US to android/gradle.properties, stopped the Gradle daemon using the JDK bundled with Android Studio, and ran the app again successfully. I used Flutter diagnostic commands, Android Studio, and AI troubleshooting guidance to solve these problems.
Q2 – Reload
I pressed Like three times and changed the AppBar title. After pressing r (hot reload), the title was updated and Likes remained at 3 because hot reload preserves the existing state. After pressing R (hot restart), Likes returned to 0 because the app restarted and the _likes variable was initialized again. I later restored the original title and confirmed that hot reload still preserved the count of 3.
Q3 – Code & Git
The _likes++ statement increases the value by one. I use setState() to notify Flutter that the state has changed and that the widget needs to be rebuilt. Without setState(), the variable could change without the displayed Likes value updating immediately.

I chose commit 39666db – Add like counter with setState. This commit changed HomePage to a StatefulWidget, added the _likes variable and _like() method, and added the Likes text and FilledButton. It allows the displayed count to increase by one each time I press Like.
Test table
Type	Input or action	Expected result	Actual
Normal	Launch the app	Title, icon, name, Likes: 0	Title, icon, name and Likes: 0 displayed correctly. (Pass)
Normal	Tap Like once	Likes: 1	Likes: 1 displayed. (Pass)
Boundary	Tap Like 20 times fast	Likes: 20, no error	Likes: 20 displayed, with no observed error. (Pass)
Boundary	Rotate to landscape	Still centred, no overflow	All elements remained centred and visible, Likes stayed at 20, and no overflow was observed. (Pass)
Reload	3 taps, then r, then R	3 after r; 0 after R	Likes stayed at 3 after hot reload and returned to 0 after hot restart. (Pass)
Failure	Close emulator, flutter run	No device found message	flutter run -d emulator-5554 reported No supported devices found with name or id matching 'emulator-5554'. Other desktop and web devices were still listed. (Pass)


AI use
I used ChatGPT to help me understand the lab instructions, explain Flutter widgets and state management, troubleshoot ADB, NDK and Gradle errors, check Dart syntax, guide Git commands, and prepare a draft of this answers file. I carried out the setup, typed and edited the code, ran the app, tested it on the Android emulator, and committed and pushed the project myself. The test results are based on my actual observations.