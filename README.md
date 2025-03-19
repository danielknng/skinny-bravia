# 🛠️ Sony Bravia TV Debloating & Performance Optimization

This guide will help you effectively remove unnecessary apps and services ("bloatware") from your Sony Bravia Android TV, significantly improving system performance. After completing the debloating process, your TV will remain fully functional with installed apps, though some built-in features like standard TV channels and accessibility services might be impacted. Carefully review each step to avoid disabling functions you require.

---

## ✅ Goals

- Remove unnecessary background processes
- Free up RAM for better performance
- Achieve a clean, distraction-free user experience

---

## 🏆 Benefits

- Faster application load times
- Enhanced UI responsiveness
- Reduced CPU and network usage
- Ad-free and clutter-free launcher

![My Local Image](./images/screenshot1.png "Example Image")
![My Local Image](./images/screenshot.png "Example Image")

---

## 📋 Table of Contents

1. [Requirements](#requirements)
2. [Preparation](#preparation)
3. [Setting Up ADB](#setting-up-adb)
4. [Identifying & Removing Bloatware](#identifying--removing-bloatware)
5. [Customizing the Launcher](#customizing-the-launcher)
6. [Optimizing System Performance](#optimizing-system-performance)
7. [Troubleshooting & Reverting Changes](#troubleshooting--reverting-changes)

---

## 🔎 Requirements

- Sony Bravia Android TV (tested on Android 9 Pie)
- Active network connection (Wi-Fi or LAN)
- Computer with ADB installed
- Basic familiarity with command-line operations

---

## 🚀 Preparation

### Enable Developer Options

- Navigate to: `Settings → Device Preferences → About`
- Tap `Build Number` **7 times** until it shows **Developer Mode Enabled**

### Enable ADB Debugging

- Navigate to: `Settings → Device Preferences → Developer Options`
- Turn on **Network Debugging**

---

## 🌐 Setting Up ADB

### Install ADB on your computer

- **Windows:** Download [Android Platform Tools](https://developer.android.com/studio/releases/platform-tools)
- **macOS:**
  ```bash
  brew install android-platform-tools
  ```
- **Linux:**
  ```bash
  sudo apt-get install android-tools-adb
  ```

### Connect to your TV via ADB

```bash
adb connect <TV_IP_ADDRESS>
```

### List installed apps

```bash
adb shell pm list packages
```

---

## 🔥 Identifying & Removing Bloatware

Below are recommended apps to remove. Use the following command structure to uninstall apps safely:

```bash
adb shell pm uninstall --user 0 <package_name>
```

### Sony Bloatware

| App Name                    | Package Name                      | Purpose                           |
| --------------------------- | --------------------------------- | --------------------------------- |
| Sony Video Frame Server     | `com.sony.dtv.videoframeserver`   | Frame rendering service           |
| Sony Demo Mode              | `com.sony.dtv.demomode`           | TV demo mode                      |
| Sony HbbTV Launcher         | `com.sony.dtv.hbbtvlauncher`      | HbbTV interface                   |
| Sony iManual                | `com.sony.dtv.imanual`            | TV user manual                    |
| Sony Smart Help             | `com.sony.dtv.smarthelp`          | Smart help service                |
| Sony Reminder Service       | `com.sony.dtv.reminderservice`    | TV reminder service               |
| Sony Discovery              | `com.sony.dtv.discovery`          | Content recommendation            |
| Sony YouView                | `com.sony.dtv.youview`            | TV content aggregation            |
| YouView Service Host        | `com.youview.tv.servicehost`      | Host for YouView service          |
| Sony Multi-Screen Demo      | `com.sony.dtv.multiscreendemo`    | Multi-screen demo                 |
| Sony Demo Support           | `com.sony.dtv.demosupport`        | Support for demo mode             |
| Sony Home Network           | `com.sony.dtv.homenetwork`        | Home network service              |
| Sony Interactive TV Utility | `com.sony.dtv.interactivetvutil`  | Interactive TV service            |
| Sony Select                 | `com.sony.dtv.sonyselect`         | Sony content store                |
| Sony Select Overlay         | `com.sony.dtv.sonyselect.overlay` | Sony content overlay              |
| Samba TV                    | `tv.samba.ssm`                    | TV content recommendation service |

### Sony System Services

| App Name                    | Package Name                         | Purpose                   |
| --------------------------- | ------------------------------------ | ------------------------- |
| Sony BraviaSync Setting     | `com.sony.dtv.braviasyncsetting`     | Bravia Sync configuration |
| Sony BraviaSync Service     | `com.sony.dtv.braviasyncservice`     | Bravia Sync service       |
| Sony Browser WebApp Runtime | `com.sony.dtv.browser.webappruntime` | Web app execution service |
| RS232 Support               | `com.sony.dtv.b2b.rs232csupport`     | RS232 support             |
| B2B service                 | `com.sony.dtv.b2b.vendorprotocol`    | Unknown b2b service       |
| PiP service                 | `com.sony.dtv.seconddispsetting`     | PiP Service (TV)          |

### Sony Enhanced Services

| App Name          | Package Name                   | Purpose                |
| ----------------- | ------------------------------ | ---------------------- |
| Sony Pro Settings | `com.sony.dtv.b2b.prosettings` | PRO settings           |
| Sony Hotel Mode   | `com.sony.dtv.b2b.hotelmode`   | PRO mode/ Hotel mode   |
| Sony Service Mode | `com.sony.dtv.servicemode`     | Developer service mode |

### Sony Diagnostics Services

| App Name                       | Package Name                          | Purpose                  |
| ------------------------------ | ------------------------------------- | ------------------------ |
| Sony Log Level Settings Vendor | `com.sony.dtv.sonyloglevelsettingvnd` | Vendor logging settings  |
| Sony Log Level Settings System | `com.sony.dtv.sonyloglevelsettingsys` | System logging settings  |
| Sony Bug Report System         | `com.sony.dtv.sonybugreportsys`       | Bug report service       |
| Sony Crash Report System       | `com.sony.dtv.system.crashlog`        | Crash report service     |
| Sony Customer Support          | `com.sony.dtv.customersupport`        | Customer support service |
| Sony DA Service                | `com.sony.dtv.da.service`             | Remote support           |

### Sony Applications

| App Name             | Package Name                    | Purpose             |
| -------------------- | ------------------------------- | ------------------- |
| Vewd Browser         | `com.vewd.core.integration.dia` | Web browser         |
| Sony Smart Media App | `com.sony.dtv.smartmediaapp`    | Media player        |
| Sony OSAT Music      | `com.sony.dtv.osat.music`       | Music player        |
| Sony Promos          | `com.sony.dtv.promos`           | Promotional content |
| Screen Mirroring     | `screenmirroring.com`           | Mirroring service   |

### Sony Television Services

| App Name                        | Package Name                            | Purpose              |
| ------------------------------- | --------------------------------------- | -------------------- |
| Sony TVX Launcher Title List    | `com.sony.dtv.tvxlauncher.titlelist`    | Recorded TV programs |
| Sony TVX Launcher Program Guide | `com.sony.dtv.tvxlauncher.programguide` | TV program guide     |
| Sony TVX                        | `com.sony.dtv.tvx`                      | TV core service      |

### Accessability Services

| App Name                | Package Name                                 | Purpose                |
| ----------------------- | -------------------------------------------- | ---------------------- |
| Sony Accessibility Text | `com.sony.dtv.common.base.AccessibilityText` | Accessibility settings |
| Google Text-to-Speech   | `com.google.android.tts`                     | Text-to-speech engine  |
| Google Talkback         | `com.google.android.marvin.talkback`         | Accessibility service  |

### Android Diagnostic Services

| App Name                    | Package Name                            | Purpose                       |
| --------------------------- | --------------------------------------- | ----------------------------- |
| Google TV Bug Report Sender | `com.google.android.tv.bugreportsender` | Send TV bug reports to Google |
| Google Feedback             | `com.google.android.feedback`           | Google feedback service       |

### Android System Services

| App Name                     | Package Name                               | Purpose                       |
| ---------------------------- | ------------------------------------------ | ----------------------------- |
| Captive Portal Login         | `com.android.captiveportallogin`           | Network captive portal        |
| VPN Dialogs                  | `com.android.vpndialogs`                   | VPN configuration             |
| Android Location Fused       | `com.android.location.fused`               | Location services             |
| Google Backup Transport      | `com.google.android.backuptransport`       | Backup data to Google         |
| Print Spooler                | `com.android.printspooler`                 | Print management service      |
| Google Backdrop              | `com.google.android.backdrop`              | Picture frame service         |
| Google SSS Authbridge        | `com.google.android.sss.authbridge`        | Google authentication bridge  |
| Google Tungsten Setup Wraith | `com.google.android.tungsten.setupwraith`  | TV setup wizard               |
| Google Webview               | `com.google.android.webview`               | Web rendering engine          |
| Google Contacts Sync         | `com.google.android.syncadapters.contacts` | Sync contacts with Google     |
| Google Calendar Sync         | `com.google.android.syncadapters.calendar` | Sync calendar with Google     |
| Google Search (Katniss)      | `com.google.android.katniss`               | Google search integration     |
| Contacts Provider            | `com.android.providers.contacts`           | Manage and store contacts     |
| Calendar Provider            | `com.android.providers.calendar`           | Calendar data provider        |
| Google TV Recommendations    | `com.google.android.tvrecommendations`     | Google TV content suggestions |
| Settings Intelligence        | `com.android.settings.intelligence`        | Google smart settings         |
| Android Dreams Basic         | `com.android.dreams.basic`                 | Screen saver service          |
| User Dictionary Provider     | `com.android.providers.userdictionary`     | Personal dictionary           |
| Android Wallpaper Backup     | `com.android.wallpaperbackup`              | Wallpaper backup service      |

### Google Applications

| App Name             | Package Name                      | Purpose                      |
| -------------------- | --------------------------------- | ---------------------------- |
| Google Play Games    | `com.google.android.play.games`   | Google Play Games service    |
| Google Play Movies   | `com.google.android.videos`       | Google movie service         |
| Google Partner Setup | `com.google.android.partnersetup` | Google partner configuration |

## 🚫 Script for all apps above

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
adb shell pm uninstall --user 0 com.google.android.partnersetup
adb shell pm uninstall --user 0 com.sony.dtv.system.crashlog
adb shell pm uninstall --user 0 com.sony.dtv.b2b.rs232csupport
adb shell pm uninstall --user 0 com.sony.dtv.b2b.vendorprotocol
adb shell pm uninstall --user 0 com.sony.dtv.seconddispsetting
adb shell pm uninstall --user 0 com.android.wallpaperbackup
```

## ➡️ Disable apps

We just want to disable these apps so if we need them again we cant just re-enable them without the need of a computer.

```bash

adb shell pm disable-user --user 0 com.google.android.apps.mediashell

adb shell pm disable-user --user 0 com.android.vending

adb shell pm disable-user --user 0 com.google.android.gms

```

## 🎨 Customizing the Launcher

Disable unwanted tabs and content in your launcher:

```bash
adb shell settings put secure tv_home_shop_content_enabled 0
adb shell settings put secure tv_home_personalized_ads_enabled 0
adb shell settings put secure tv_home_content_suggestions_enabled 0
adb shell settings put secure tv_home_promotion_tile_enabled 0
```

Clear the launcher data for changes to apply:

```bash
adb shell pm clear com.google.android.tvlauncher
```

---

## 🚀 Optimizing System Performance

Apply these settings to enhance responsiveness:

```bash
adb shell setprop persist.sys.input_lag 0
adb shell settings put global game_mode 1
adb shell settings put global window_animation_scale 0.5
adb shell settings put global transition_animation_scale 0.5
adb shell settings put global animator_duration_scale 0.5
```

---

## ⚙️ Troubleshooting & Reverting Changes

### Reinstall apps

```bash
adb shell cmd package install-existing <package_name>
```

### Reactivate disabled apps

```bash
adb shell pm enable <package_name>
```

### Issues after enabling Play Services

Re-enabling Google Play Services may cause extra tabs to reappear. To revert:

```bash
adb shell pm clear com.google.android.tvlauncher
```
