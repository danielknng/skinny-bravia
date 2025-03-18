# 🛠️ Sony Bravia TV Debloating & Performance Optimization  
*This guide will massively debloat your Sony Bravia TV! After debloatig you can use all installed apps, but you wont be able to watch normal television, use Accessibility options and some other functions. Please refer to the table below to make sure you wont disable functions you need. *  

---

The screenshots below show my launcher after debloating. The launcher was not downgraded or replaced. 

![My Local Image](./images/screenshot.png "Example Image")
![My Local Image](./images/screenshot1.png "Example Image")

## ✅ Goal of the Guide  
This guide explains how to remove unnecessary background services and bloatware from a Sony Bravia TV (Android TV) to improve performance, free up RAM, and create a clean, distraction-free user experience. 

---
## 🏆 Benefits of Debloating  
✔️ More available RAM → Faster app loading  
✔️ Improved UI responsiveness  
✔️ Less background activity → Reduced network and CPU load  
✔️ Customized launcher without ads or unnecessary content  
---

## 🔎 Device Requirements  
- Sony Bravia TV with **Android TV** (tested with Android 9 Pie)  
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
---

## 


### 🔥 Recommended Bloatware to Remove:
| App Name                                 | Package Name                                 | Purpose                                      |
|------------------------------------------|----------------------------------------------|----------------------------------------------|
| Sony Video Frame Server                 | `com.sony.dtv.videoframeserver`              | Frame rendering service                      |
| Android Dreams Basic                    | `com.android.dreams.basic`                   | Screen saver service                         |
| Google Backdrop                         | `com.google.android.backdrop`                | Chromecast backdrop service                  |
| Screen Mirroring                        | `screenmirroring.com`                        | Mirroring service                            |
| Sony BraviaSync Setting                 | `com.sony.dtv.braviasyncsetting`             | Bravia Sync configuration                   |
| Sony BraviaSync Service                 | `com.sony.dtv.braviasyncservice`             | Bravia Sync service                          |
| Captive Portal Login                    | `com.android.captiveportallogin`             | Network captive portal                      |
| Sony Customer Support                   | `com.sony.dtv.customersupport`               | Customer support service                     |
| Sony Demo Mode                          | `com.sony.dtv.demomode`                      | TV demo mode                                 |
| Sony Multi-Screen Demo                  | `com.sony.dtv.multiscreendemo`               | Multi-screen demo                           |
| Sony Demo Support                       | `com.sony.dtv.demosupport`                   | Support for demo mode                       |
| Print Spooler                           | `com.android.printspooler`                   | Print management service                    |
| Sony Reminder Service                   | `com.sony.dtv.reminderservice`               | TV reminder service                         |
| Sony DA Service                         | `com.sony.dtv.da.service`                    | Direct access service                       |
| Google Backup Transport                 | `com.google.android.backuptransport`          | Backup data to Google                       |
| Google Play Games                       | `com.google.android.play.games`               | Google Play Games service                   |
| Sony HbbTV Launcher                    | `com.sony.dtv.hbbtvlauncher`                 | HbbTV interface                             |
| Sony iManual                            | `com.sony.dtv.imanual`                       | TV user manual                              |
| Sony Smart Help                         | `com.sony.dtv.smarthelp`                     | Smart help service                          |
| Sony Home Network                       | `com.sony.dtv.homenetwork`                   | Home network service                        |
| Sony Interactive TV Utility             | `com.sony.dtv.interactivetvutil`             | Interactive TV service                      |
| Android Location Fused                 | `com.android.location.fused`                 | Location services                           |
| Sony TVX Launcher Title List            | `com.sony.dtv.tvxlauncher.titlelist`          | Title list for TVX                         |
| Sony Smart Media App                    | `com.sony.dtv.smartmediaapp`                 | Smart media service                         |
| Sony OSAT Music                         | `com.sony.dtv.osat.music`                    | Music service                               |
| Sony Hotel Mode                         | `com.sony.dtv.b2b.hotelmode`                 | Hotel mode configuration                    |
| Sony TVX Launcher Program Guide         | `com.sony.dtv.tvxlauncher.programguide`       | TVX program guide                           |
| Sony Pro Settings                       | `com.sony.dtv.b2b.prosettings`               | Pro settings for TV                         |
| Sony Select                             | `com.sony.dtv.sonyselect`                    | Sony content store                          |
| Sony Accessibility Text                 | `com.sony.dtv.common.base.AccessibilityText`  | Accessibility settings                      |
| Sony TVX                                | `com.sony.dtv.tvx`                           | TVX core service                            |
| Sony Discovery                          | `com.sony.dtv.discovery`                     | Content recommendation                      |
| Sony YouView                            | `com.sony.dtv.youview`                       | TV content aggregation                      |
| Sony Promos                             | `com.sony.dtv.promos`                        | Promotional content                         |
| YouView Service Host                    | `com.youview.tv.servicehost`                  | Host for YouView service                    |
| Sony Browser WebApp Runtime             | `com.sony.dtv.browser.webappruntime`         | Web app execution service                   |
| VPN Dialogs                             | `com.android.vpndialogs`                     | VPN configuration                           |
| Sony Log Level Settings Vendor          | `com.sony.dtv.sonyloglevelsettingvnd`         | Vendor logging settings                     |
| Sony Log Level Settings System          | `com.sony.dtv.sonyloglevelsettingsys`         | System logging settings                     |
| Sony Bug Report System                  | `com.sony.dtv.sonybugreportsys`               | Bug report service                          |
| Google Tungsten Setup Wraith            | `com.google.android.tungsten.setupwraith`     | TV setup wizard                             |
| Settings Intelligence                  | `com.android.settings.intelligence`            | Google smart settings                       |
| Sony Service Mode                       | `com.sony.dtv.servicemode`                    | Developer service mode                      |
| Google SSS Authbridge                   | `com.google.android.sss.authbridge`            | Google authentication bridge                |
| Samba TV                                | `tv.samba.ssm`                                | TV content recommendation service            |
| User Dictionary Provider                | `com.android.providers.userdictionary`         | Personal dictionary provider                 |
| Google Feedback                         | `com.google.android.feedback`                  | Google feedback service                     |
| Contacts Provider                       | `com.android.providers.contacts`               | Manage and store contacts                   |
| Calendar Provider                       | `com.android.providers.calendar`               | Calendar data provider                      |
| Vewd Browser                            | `com.vewd.core.integration.dia`                | Web browsing platform                       |
| Google Contacts Sync                    | `com.google.android.syncadapters.contacts`     | Sync contacts with Google                   |
| Google Text-to-Speech                   | `com.google.android.tts`                      | Text-to-speech engine                       |
| Google Play Movies                      | `com.google.android.videos`                   | Google movie service                        |
| Google Partner Setup                    | `com.google.android.partnersetup`              | Google partner configuration                |
| Google Calendar Sync                    | `com.google.android.syncadapters.calendar`     | Sync calendar with Google                   |
| Google Search (Katniss)                 | `com.google.android.katniss`                  | Google search integration                   |
| Google TV Bug Report Sender             | `com.google.android.tv.bugreportsender`        | Send TV bug reports to Google               |
| Google TV Recommendations               | `com.google.android.tvrecommendations`         | Google TV content suggestions               |
| Google Webview                          | `com.google.android.webview`                   | Web rendering engine                        |
| Google Talkback                         | `com.google.android.marvin.talkback`            | Accessibility service                       |
| Sony Select Overlay                     | `com.sony.dtv.sonyselect.overlay`              | Sony content overlay                        |




### ➡️ Remove Bloatware
```bash
adb shell pm uninstall --user 0 com.sony.dtv.videoframeserver
adb shell pm uninstall --user 0 com.android.dreams.basic
adb shell pm uninstall --user 0 com.google.android.backdrop
adb shell pm uninstall --user 0 screenmirroring.com
adb shell pm uninstall --user 0 com.sony.dtv.braviasyncsetting
adb shell pm uninstall --user 0 com.sony.dtv.braviasyncservice
adb shell pm uninstall --user 0 com.android.captiveportallogin
adb shell pm uninstall --user 0 com.sony.dtv.customersupport
adb shell pm uninstall --user 0 com.sony.dtv.demomode
adb shell pm uninstall --user 0 com.sony.dtv.multiscreendemo
adb shell pm uninstall --user 0 com.sony.dtv.demosupport
adb shell pm uninstall --user 0 com.android.printspooler
adb shell pm uninstall --user 0 com.sony.dtv.reminderservice
adb shell pm uninstall --user 0 com.sony.dtv.da.service
adb shell pm uninstall --user 0 com.google.android.backuptransport
adb shell pm uninstall --user 0 com.google.android.play.games
adb shell pm uninstall --user 0 com.sony.dtv.hbbtvlauncher
adb shell pm uninstall --user 0 com.sony.dtv.imanual
adb shell pm uninstall --user 0 com.sony.dtv.smarthelp
adb shell pm uninstall --user 0 com.sony.dtv.homenetwork
adb shell pm uninstall --user 0 com.sony.dtv.interactivetvutil
adb shell pm uninstall --user 0 com.android.location.fused
adb shell pm uninstall --user 0 com.sony.dtv.tvxlauncher.titlelist
adb shell pm uninstall --user 0 com.sony.dtv.smartmediaapp
adb shell pm uninstall --user 0 com.sony.dtv.osat.music
adb shell pm uninstall --user 0 com.sony.dtv.b2b.hotelmode
adb shell pm uninstall --user 0 com.sony.dtv.tvxlauncher.programguide
adb shell pm uninstall --user 0 com.sony.dtv.b2b.prosettings
adb shell pm uninstall --user 0 com.sony.dtv.sonyselect
adb shell pm uninstall --user 0 com.sony.dtv.common.base.AccessibilityText
adb shell pm uninstall --user 0 com.sony.dtv.tvx
adb shell pm uninstall --user 0 com.sony.dtv.discovery
adb shell pm uninstall --user 0 com.sony.dtv.youview
adb shell pm uninstall --user 0 com.sony.dtv.promos
adb shell pm uninstall --user 0 com.youview.tv.servicehost
adb shell pm uninstall --user 0 com.sony.dtv.browser.webappruntime
adb shell pm uninstall --user 0 com.android.vpndialogs
adb shell pm uninstall --user 0 com.sony.dtv.sonyloglevelsettingvnd
adb shell pm uninstall --user 0 com.sony.dtv.sonyloglevelsettingsys
adb shell pm uninstall --user 0 com.sony.dtv.sonybugreportsys
adb shell pm uninstall --user 0 com.google.android.tungsten.setupwraith
adb shell pm uninstall --user 0 com.android.settings.intelligence
adb shell pm uninstall --user 0 com.sony.dtv.servicemode
adb shell pm uninstall --user 0 com.google.android.sss.authbridge
adb shell pm uninstall --user 0 tv.samba.ssm
adb shell pm uninstall --user 0 com.android.providers.userdictionary
adb shell pm uninstall --user 0 com.google.android.feedback
adb shell pm uninstall --user 0 com.android.providers.contacts
adb shell pm uninstall --user 0 com.android.providers.calendar
adb shell pm uninstall --user 0 com.vewd.core.integration.dia
adb shell pm uninstall --user 0 com.google.android.syncadapters.contacts
adb shell pm uninstall --user 0 com.google.android.tts
adb shell pm uninstall --user 0 com.google.android.videos
adb shell pm uninstall --user 0 com.google.android.partnersetup
adb shell pm uninstall --user 0 com.google.android.syncadapters.calendar
adb shell pm uninstall --user 0 com.google.android.katniss
adb shell pm uninstall --user 0 com.google.android.tv.bugreportsender
adb shell pm uninstall --user 0 com.google.android.tvrecommendations
adb shell pm uninstall --user 0 com.google.android.webview
adb shell pm uninstall --user 0 com.google.android.marvin.talkback
adb shell pm uninstall --user 0 com.sony.dtv.sonyselect.overlay
```


### ➡️ Disable apps 
We want to just disable these apps so if we need them again we cant just enable them again without the need of a computer. 
```bash
adb shell pm disable-user --user 0 com.google.android.apps.mediashell
adb shell pm disable-user --user 0 com.android.vending
adb shell pm disable-user --user 0 com.google.android.gms
```

### ➡️ Clean Launcher Data 
```bash
adb shell pm clear com.google.android.tvlauncher
```

### Tweak the Launcher (Optional, may not have an effect)
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
adb shell cmd package install-existing <package_name>
```





