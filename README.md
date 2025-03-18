# 🛠️ Sony Bravia TV Debloating & Performance Optimization  
*A Guide to Removing Bloatware, Customizing the Launcher, and Improving Overall Performance*  

---

![My Local Image](./images/screenshot.png "Example Image")
![My Local Image](./images/screenshot1.png "Example Image")

## ✅ Goal of the Guide  
This guide explains how to remove unnecessary background services and bloatware from a Sony Bravia TV (Android TV) to improve performance, free up RAM, and create a clean, distraction-free user experience.  

---

## 🔎 Device Requirements  
- Sony Bravia TV with **Android TV** (tested with Android 9 Pie)  
- MediaTek processor (results may vary with other chipsets)  
- Active network connection (Wi-Fi or LAN)  
- Computer with **ADB (Android Debug Bridge)** installed  
- Basic knowledge of command-line interfaces  

## 📝 Prerequisites
- The device is already set-up and you have all apps you need installed from Google Play Store. This is neccessary because we will disable Google Play Services and Google Play Store.You can enable it again if you need to. 

---

## ⚠️ Warnings  
> ⚠️ **Root access is not required**, but some steps may alter factory settings.  
> ⚠️ Disabling critical system apps can affect system stability.  
> ⚠️ Some updates may fail after disabling certain services, even thought I didnt experience any issues.

---

## 🏆 Benefits of Debloating  
✔️ More available RAM → Faster app loading  
✔️ Improved UI responsiveness  
✔️ Less background activity → Reduced network and CPU load  
✔️ Customized launcher without ads or unnecessary content  

---

## 📋 Structure of the Guide  
The guide is divided into the following sections:  

1. [Preparation](#preparation)  
2. [Set Up ADB Access](#set-up-adb-access)  
3. [List Installed Apps](#list-installed-apps)  
4. [Identify and Remove Bloatware](#identify-and-remove-bloatware)  
5. [Customize the Launcher](#customize-the-launcher)  
6. [Prevent Automatic Background Start](#prevent-automatic-background-start)  
7. [Optimize RAM and CPU Usage](#optimize-ram-and-cpu-usage)  
8. [Troubleshooting and Reverting Changes](#troubleshooting-and-reverting-changes)  

---

## 1. 🚀 Preparation  
Before starting, make sure to:  
- Connect the TV to the same Wi-Fi network as your computer (or use a USB cable).  
- Enable **Developer Options** on your TV:  
    - Go to **Settings → Device Preferences → About**  
    - Tap **Build Number** 7 times until "Developer Mode Enabled" appears.  

- Enable **ADB Debugging** on your TV:
    - Go to **Settings → Device Preferences → Developer Options**  
    - Enable **Network Debugging**

---

## 2. 🌐 Set Up ADB Access  
### ➡️ Install ADB  
1. Install ADB on your computer (if not installed):  
    - **Windows:**  
      Download the platform tools from the [official Android developer site](https://developer.android.com/studio/releases/platform-tools).  
    - **MacOS:**  
      ```bash
      brew install android-platform-tools
      ```  
    - **Linux:**  
      ```bash
      sudo apt-get install android-tools-adb
      ```  

### ➡️ Connect to the TV  
 
```bash
adb connect <TV_IP>
```

Now you are connected to your TV via ADB. We are not continuing to list installed apps. Below I curated a list of apps that can be safely removed without affecting the system. 
### ➡️ List packages 

```bash
adb shell pm list packages
```


### 🔥 Recommended Bloatware to Remove:
If you follow the list below you wont be able to use the following features of the TV:
- Google Play Store
- Google Play Services (Your account wont be displayed at all, but wont get deleted)
- Google Assistant
- Bravia Sync
- Google Movies
- Android default Screen Saver
- Discover-Function from Sony
- Television 
- 

| App Name                                 | Package Name                                 | Purpose                                      | Safe to Remove? |
|------------------------------------------|----------------------------------------------|----------------------------------------------|-----------------|
| Google Media Shell                      | `com.google.android.apps.mediashell`         | Media streaming shell                       | ✅ Yes           |
| Google Search (Katniss)                 | `com.google.android.katniss`                 | Google search integration                   | ✅ Yes           |
| Calendar Provider                       | `com.android.providers.calendar`             | Calendar data provider                      | ✅ Yes           |
| Sony Bugreport System                   | `com.sony.dtv.sonybugreportsys`              | System bug report service                   | ✅ Yes           |
| Google Setup Wraith                     | `com.google.android.tungsten.setupwraith`    | Setup wizard for TV                         | ✅ Yes           |
| Sony Browser WebApp Runtime             | `com.sony.dtv.browser.webappruntime`         | Web app execution service                   |  ✅ Yes (if not needed)          |
| Google Play Store                       | `com.android.vending`                        | Google app store                            | ✅ Yes (if not needed) |
| Google Talkback                         | `com.google.android.marvin.talkback`          | Accessibility service                       | ✅ Yes           |
| Sony Service Mode                       | `com.sony.dtv.servicemode`                   | Developer service mode                      | ✅ Yes           |
| Vewd Browser                            | `com.vewd.core.integration.dia`              | Web browsing platform                       | ✅ Yes           |
| Settings Intelligence                   | `com.android.settings.intelligence`           | Google smart settings                       | ✅ Yes           |
| Google TV Recommendations               | `com.google.android.tvrecommendations`        | Google TV content suggestions               | ✅ Yes           |
| Google Webview                          | `com.google.android.webview`                  | Web rendering engine                        | ✅ Yes           |
| YouView Service Host                    | `com.youview.tv.servicehost`                  | TV content aggregation service               | ✅ Yes           |
| Google Contacts Sync                    | `com.google.android.syncadapters.contacts`     | Sync contacts with Google                   | ✅ Yes           |
| Google Play Services                    | `com.google.android.gms`                      | Google core services                        | ✅ Yes         |
| Google Text-to-Speech                   | `com.google.android.tts`                      | Text-to-speech engine                       | ✅ Yes           |
| Google Partner Setup                    | `com.google.android.partnersetup`             | Google partner configuration                | ✅ Yes           |
| Google Play Movies                      | `com.google.android.videos`                   | Google movie service                        | ✅ Yes           |
| Sony Log Level Setting System           | `com.sony.dtv.sonyloglevelsettingsys`         | System logging configuration                | ✅ Yes           |
| Sony Log Level Setting Vendor           | `com.sony.dtv.sonyloglevelsettingvnd`         | Vendor logging configuration                | ✅ Yes           |
| Google Feedback                         | `com.google.android.feedback`                 | Google feedback service                     | ✅ Yes           |
| Google Calendar Sync                    | `com.google.android.syncadapters.calendar`     | Sync calendar with Google                   | ✅ Yes           |
| Google TV Bug Report Sender             | `com.google.android.tv.bugreportsender`        | Send TV bug reports to Google               | ✅ Yes           |
| Samba TV                                | `tv.samba.ssm`                                | TV content recommendation service            | ✅ Yes (if not needed)          |
| Sony Smart Home Settings                | `com.sony.dtv.smarthomesettings`              | Smart home integration                      | ✅ Yes           |
| Google SSS Authbridge                  | `com.google.android.sss.authbridge`            | Google authentication bridge                | ✅ Yes           |
| VPN Dialogs                             | `com.android.vpndialogs`                      | VPN connection dialogs                      | ✅ Yes (if not needed)           |
| User Dictionary Provider                | `com.android.providers.userdictionary`         | Personal dictionary provider                 | ✅ Yes           |
| Contacts Provider                       | `com.android.providers.contacts`               | Manage and store contacts                   | ✅ Yes           |



### ➡️ Remove Bloatware
```bash
adb shell pm uninstall --user 0 com.google.android.apps.mediashell
adb shell pm uninstall --user 0 com.google.android.katniss
adb shell pm uninstall --user 0 com.android.providers.calendar
adb shell pm uninstall --user 0 com.sony.dtv.sonybugreportsys
adb shell pm uninstall --user 0 com.google.android.tungsten.setupwraith
adb shell pm uninstall --user 0 com.sony.dtv.browser.webappruntime
adb shell pm uninstall --user 0 com.android.vending
adb shell pm uninstall --user 0 com.google.android.marvin.talkback
adb shell pm uninstall --user 0 com.sony.dtv.servicemode
adb shell pm uninstall --user 0 com.vewd.core.integration.dia
adb shell pm uninstall --user 0 com.android.settings.intelligence
adb shell pm uninstall --user 0 com.google.android.tvrecommendations
adb shell pm uninstall --user 0 com.google.android.webview
adb shell pm uninstall --user 0 com.youview.tv.servicehost
adb shell pm uninstall --user 0 com.google.android.syncadapters.contacts
adb shell pm uninstall --user 0 com.google.android.gms
adb shell pm uninstall --user 0 com.google.android.tts
adb shell pm uninstall --user 0 com.google.android.partnersetup
adb shell pm uninstall --user 0 com.google.android.videos
adb shell pm uninstall --user 0 com.sony.dtv.sonyloglevelsettingsys
adb shell pm uninstall --user 0 com.sony.dtv.sonyloglevelsettingvnd
adb shell pm uninstall --user 0 com.google.android.feedback
adb shell pm uninstall --user 0 com.google.android.syncadapters.calendar
adb shell pm uninstall --user 0 com.google.android.tv.bugreportsender
adb shell pm uninstall --user 0 tv.samba.ssm
adb shell pm uninstall --user 0 com.sony.dtv.smarthomesettings
adb shell pm uninstall --user 0 com.google.android.sss.authbridge
adb shell pm uninstall --user 0 com.android.vpndialogs
adb shell pm uninstall --user 0 com.android.providers.userdictionary
adb shell pm uninstall --user 0 com.android.providers.contacts

```

### Tweak the Launcher
```bash
adb shell settings put secure tv_home_shop_content_enabled 0
adb shell settings put secure tv_home_personalized_ads_enabled 0
adb shell settings put secure tv_home_content_suggestions_enabled 0
adb shell settings put secure tv_home_promotion_tile_enabled 0
```

### Delete Launcher App Data 
```bash
adb shell pm clear com.google.android.tvlauncher
```

### Improve overall performance 
```bash
adb shell setprop persist.sys.input_lag 0
adb shell settings put global game_mode 1
adb shell settings put global window_animation_scale 0.5
adb shell settings put global transition_animation_scale 0.5
adb shell settings put global animator_duration_scale 0.5
```



## Troubleshooting and Reverting Changes

### Reinstall any app 
```bash
adb shell cmd package install-existing com.sony.dtv.scrums.action
```





