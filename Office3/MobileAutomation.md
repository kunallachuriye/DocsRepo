# Mobile Automation

## Initial Setup

* Developer option has to be enabled in the device
* USB Debugging Should be on
* ***Appium*** has to be installed. ***Desktop version*** as well as the ***appium node package***.
* Install Android SDK. And set the following path.
 ```cmd
   C:\Users\test.user\AppData\Local\Android\Sdk\platform-tools;
   C:\Users\test.user\AppData\Local\Android\Sdk\tools\bin;
 ```
 * Check if ADB commands work or not

## Steps
* ***STEP 1:*** Connect the Mobile Device

* ***STEP 2:*** CMD --> adb devices (You will be able to see the devices)
```cmd
   * daemon not running; starting now at tcp:5037
   * daemon started successfully
   List of devices attached
   16898cd3        device
```

* ***STEP 3:*** Install The Application
  ** Method 1:<br/>
  Install it from playstore<br/>

  ** Method 2:<br/>
  By Command ***adb install appname***<br/>

  ** Method 3:<br/>
  By Drag and Drop the application into the Emulator<br/>
 
 

### For Android Ways to get the app package and App activity
##### Method 1:
For Mac/Linux:
```cmd
   adb shell dumpsys window | grep -E 'mCurrentFocus' 
```
For Windows:
```cmd
adb shell dumpsys window | find "mCurrentFocus"
```
##### Method 2:
Trace the entire Mobile Logs
```cmd
   adb logcat
```
##### Method 3:
If we have the apk file of the application.<br/>
Then we can extract that and see into the Manifest.xml and find the **Launcher Activity**

##### Method 4:
Install any 3rd party applcation ***App Info APK**, and it will show the app package and app activity of all the Applications.

### Verify the App package and app name
```cmd
adb shell am start -W -n com.package.name/com.zinier.app.ui.activities.activity -S -a android.intent.action.MAIN -c android.intent.category.LAUNCHER -f 0x10200000
```
If the above command is successful the we have correctly foud the app-package and app-activity




```json
{
  "deviceName": "16898cd3",
  "appPackage": "com.name.app",
  "appActivity": "com..app.ui.activities.login.LoginActivity",
  "platformName": "android"
}
```