# Android C/C++ NDK - Native executable

Download **Android NDK**  
https://developer.android.com/ndk/downloads  

Set `$NDK_HOME` to the NDK directory (`/path/to/android-ndk-r28`).  
Set `$NDK_PROJECT_PATH` to this folder (`/path/to/hello-android`).  

Run `ndk-build`. It will create executables in `hello/libs/` for each architecture defined in `Application.mk`:`APP_ABI`.  

```sh
git clone https://github.com/username/hello-android
cd hello-android
export NDK_HOME=/path/to/android-ndk-r28
export NDK_PROJECT_PATH=$(pwd)
/path/to/android-ndk-r28/ndk-build
```

Get **adb** (Android Debug Bridge) from SDK Manager (Android Studio) or from Platform Tools (precompiled - preferred).  
https://developer.android.com/tools/adb  
https://developer.android.com/studio/intro/update#sdk-manager  
https://developer.android.com/tools/releases/platform-tools (preferred)  

Enable developer options on your Android device (phone, tablet, werable, ...).  
https://developer.android.com/studio/debug/dev-options#enable  

Connect the device in the computer with a cable that supports data transfer (some charging cables are not capable of transfer data).  

Start `adk` server.  
Push the compiled executable to the `/tmp` folder in the device.  
Enter the device shell.  
Run the problem from the device.  

```sh
adb kill-server  # in case it is running
adb start-server
adb push /path/to/hello-android/libs/arm64-v8a/hello /tmp
adb shell
# inside the device
cd /tmp
./hello
```
