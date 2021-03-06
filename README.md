![Header](/header.png?raw=true)
# 🗜 Mobile Toolkit
📲 **Control Android and iOS devices** or Emulators/Simulators using terminal commands<br>

🛠 **Take screeshots, change developer settings**, gather app & device intel<br>

⚙️ **Manage mobile applications** - install, restart, wipe data and much more<br>

📋 **Handle multiple devices effortlessly** - select from list or target all connected devices<br>

⏳ **Save your precious time** - stop doing repetitive tasks manually<br>

🔄 **Automatic update** - get new features and fixes ASAP<br>

⁉️ **Submit issue** - report bugs, bring inspiration, ask questions<br>

🤝 [Pull request contribution](https://github.com/IntergalacticPenguin/mobile-toolkit/blob/master/.github/CONTRIBUTING.md "contribution rules") **is highly appreciated, see** [Issues section](https://github.com/IntergalacticPenguin/mobile-toolkit/issues)<br>

⭐️ **Love Mobile Toolkit? -> Hit the star button and bring me joy!**<br>

# 💻 Installation
1. **Open terminal**
2. **Clone this repository** `git clone https://github.com/IntergalacticPenguin/mobile-toolkit.git`
3. **Setup Android** tools
	* [Download](https://developer.android.com/studio/ "Android Studio") and install **Android Studio** or **Android command line tools**
	* Add the absolute path to the **platform-tools** folder to **PATH** variable in **.bash_profile** `PATH=$PATH:/Users/dummyuser/Library/Android/sdk/platform-tools export PATH`
	* **Allow USB debugging** on your device, connect it and **authorize** your computer (click OK on device screen)
4. **Setup iOS** tools
	* Install latest **Xcode and iOS command line tools** using App Store
	* [Install](https://brew.sh/ "Homberew") **Homebrew** package manager
	* Install [usbmuxd](https://github.com/libimobiledevice/usbmuxd "usbmuxd"), [libimobiledevice](https://github.com/libimobiledevice/libimobiledevice "libimobiledevice") and  [ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller "ideviceinstaller")  `brew install --HEAD usbmuxd && brew install --HEAD libimobiledevice && brew install --HEAD ideviceinstaller`
	* Mount developer image on your device **-> connect iOS device to USB**, **authorize** your computer (click "Trust" on device screen) and **run Xcode**
5. (Optional) Use following **commands in any directory** in your terminal
	* Edit your **.bash_profile** file (or .zshrc if you have zsh shell) in your home directory `nano ~/.bash_profile`
	* Add the path to the script folders to **PATH** variable in **.bash_profile** (or equivalent file) -> **insert the following lines at the end of the file**, make sure to **replace "dummyuser" with your profile name and use proper path**
	`PATH=$PATH:/Users/dummyuser/Repositories/Shell/mobile-toolkit/android`
	`PATH=$PATH:/Users/dummyuser/Repositories/Shell/mobile-toolkit/ios`

_The scripts are primarily designed for macOS, but majority of functions should work on any Unix system._

# 🤖 Android scripts

## Capture screen

### 📸 ascreenshot
* `ascreenshot` Save screenshot to ~/Desktop
* `ascreenshot -a` Take screenshot on all connected devices

### 🎥 arecord
1. `arecord` Record screen
2. End recording using `ctrl + c`
3. Save screen video footage to ~/Desktop
  * `arecord <custom-name>` Specify your own filename by passing it as argument

## Control device

### ✏️ apaste
`apaste "john.doe@fakemail.com" password1 "5005 1002 3332 1112" "2/19" 5004`

* `apaste <text>` Insert text into currently focused field
* `apaste "john.doe@fakemail.com" password1 ` Every additional argument will be inserted into subsequent field
* `apaste "This is sample multi-word text."` use "" to insert multi-word text into one field
* `apaste -l` Paste Lorem Ipsum paragraph

### 🌐 aurl
* `aurl "google.com"` Open link in web browser or corresponding application

### 📐 abounds
* `abounds` Display layout bounds
	* Press ENTER to turn off
* `abounds -k` Toggle layout bounds visibility
* App restart may be necessary on lower APIs

### 🚗 aanimationspeed
* `aanimationspeed` set slow animation speed
* `aanimationspeed <speed>` set animation speed to \<speed> times slower than default
	* Press ENTER to reset to default
* `afontscale <scale> -k` save changed settings

### 🔠 afontscale
* `afontscale` set font scale to large (1.3x bigger than default)
* `afontscale <scale>` set font scale to \<scale> times larger than default
	* Press ENTER to reset to default
* `afontscale <scale> -k` save changed settings

### 🎹 acontrol
* `scrpy` start [scrcpy](https://github.com/Genymobile/scrcpy "scrcpy") session
* [scrcpy](https://github.com/Genymobile/scrcpy "scrcpy") provides realtime device screen mirroring and operation

### 📷 acamera
* Start the default camera application

### ⚡️ awireless
* Enable or disable wireless ADB connection
* Use ADB and toolkit without having USB cable attached

## Manage packages

### 🚀 alaunch
* `alaunch` List third-party apps and choose one to run it
* `alaunch -s` List all available apps (including os pre-installed) and choose one to run it
* `alaunch com.dummy.package.name.app` Run app by package name

### 🕵️ aappinfo
* `aappinfo` List foreground app information
  * Package name
	* Version
	* Last update
	* minSdk and targetSdk
	* Permissions
* (Optional) Open application settings
* `aappinfo com.dummy.package.name.app` Target specific app by passing package name as argument

### 🔪 akill
* `akill` Restart the foreground app
* `akill com.dummy.package.name.app` Target specific app by passing package name as argument

### 🧽 aerase
* `aerase` Delete all local data of the foreground app and restart it
* `aerase com.dummy.package.name.app` Target specific app by passing package name as argument

### 🚚 ainstall
* `ainstall some-app-file.apk` Install and run .apk
* `ainstall -a some-app-file.apk` Install and run .apk on all connected devices

### 🗑 auninstall
* `auninstall` Uninstall third-party app, choose from the list
* `auninstall com.dummy.package.name.app` pass package name as argument
* `auninstall -a` Uninstall all-third party packages
	* Skips some essential apps, edit IGNORED_PACKAGES in this script to customize the list to your needs

### 🔥 awipe
* Wipe internal storage (/mnt/sdcard directory) and delete all third-party apps

### 🐁 apermissionreset
* Revoke ALL runtime permissions for ALL (even system) apps

### 🛍 agoogleplay
* `agoogleplay "Dummy App"` Search for "Dummy App" on Google Play
* `agoogleplay` Search for currently foreground app on Google Play

### 🏭 abuildproject
* `abuildproject` Build, install and run Android project located in current directory
* `abuildproject <relative-path>` Build, install and run Android project located in \<relative-path>

## Manage device

### ⚙️ aoptions
* `aoptions` Open system settings on a specific activity
* You can choose from quick presets
	* Developer settings
	* Locale settings
	* Date & time
	* Wifi settings
	* Storage management
	* Power usage
	* Root settings activity
* `aoptions A` Choose from exhaustive list of all available options
* `aoptions 1,2,3... | dev | locale | date | wifi | storage | power` Use a preset, choose one

### 📜 alog
* `alog` Print system log output
* `alog -f <package-name>` Filter log by package name

### 💥 acrash
* `acrash` Print log output containing application crashes only
* `acrash <line-count>` Print \<line-count> lines above and below crash log

### 📋 acheckdevice
* Print genereal device information
* Perform basic safety-checks and toggle "testing firendly" settings
  * 10 minutes screen timeout
  * Highest brightness
  * Automatic date
  * Disabled notification sounds
  * Internet connectivity and WIFI name
  * Font scale
  * enUS locale
* (Optional) Search for the device on [GSMArena](https://www.gsmarena.com/ "GSMArena")

### 😎 aservices
* Print running background services
* Search for more information via Google

### ♻ areboot
* Reboot the device

### 📱 aemulator
* Android emulator supports all listed scripts by default + extra actions listed below
* `aeimulator <option>` Handle various Android emulator activites
  * `start` - choose and launch installed emulator
  * `gprs | edge | 3g` - simulate network latency, choose one
  * `call <number>` - receive fake call
  * `sms <number> <text>` - receive fake sms
  * `gps <lat> <long>` - set manual GPS location
  * `battery <0-100>` - set battery level
  * `telnet <command>` - call command via telnet
	   * example commands `event | redir | sensor | physics | finger | rotate | fold | unfold...` see [Android emulator documentation](https://developer.android.com/studio/run/emulator-console#console-session) for more information

# 🍎 iOS scripts

## Capture screen

### 📸 iscreenshot
* `iscreenshot` Save screenshot to ~/Desktop
* `iscreenshot -a` Take screenshot on all connected devices

### 🎥 irecord
* Run QuickTime and open video source picker (so you can choose a device right away)
  * You may have to allow some system permission, so the script can access the picker

### 🖼 igif
**Required**: Install [ffmpeg](https://www.ffmpeg.org/ "ffmpeg") `brew install ffmpeg`

1. Record screen (take as many screenshots per second as possible) to ~/Desktop
2. End recording using `ctrl + c`
3. Compose .mp4 from screenshots and save it to ~/Desktop
4. (Optional) Delete screenshots
* Specify your own filename by passing it as argument

## Manage applications
### 🚚 iinstall
* `iinstall some-app-file.ipa` Install .ipa (make sure to use properly signed build)
* `iinstall -a some-app-file.ipa` Install .ipa to all connected devices

### 🗑 iuninstall
* `iuninstall` Uninstall third-party app, choose from the list
* `iuninstall com.dummy.package.name.app` pass bundle name as argument
* `iuninstall -a` Uninstall all third-party packages
  * Skips some essential apps, edit IGNORED_PACKAGES in this script to customize the list to your needs

## Manage device

### 📜 ilog
* `ilog` Open console log output
* Examine macOS or iOS system logs

### 💥 icrashlogs
* Gather crash logs from the device to ~/Desktop (be patient 😅)
* Choose whether to keep the logs on the device afterwards
* You can import these logs to Xcode to make them more readable via symbolication
  * Open relevant project in Xcode
  * Click on Window > Devices and Simulators > View Device Logs
  * Drag the .crash file onto the log list
  * Readable crash log should appear in the list

### 📋 icheckdevice
* Print device information
* (Optional) Search for the device on [GSMArena](https://www.gsmarena.com/ "GSMArena")

### ♻ ireboot
* Reboot the device

### 📱 isimulator
* Simulator has limited functionality (no camera, biometrics, Appstore...), but **offers some extra options, unavailable on physical iOS devices**
* `isimulator <option>` Handle various simulator related activites
  * `start` - choose and launch installed simulator
  * `screenshot` - save screenshot to ~/Desktop
  * `record` - save screen recording to ~/Desktop (full resolution and frame rate, without QuickTime hassle)
  * `paste <text>` - insert text into pasteboard
  * `import <file>` - import image or video to simulator gallery app
  * `log` - print simulator log
  * `url <url>` - open link in web browser or corresponding application
  * `wipe` - wipe all simulator data
  * `battery <0-100>` - set battery level displayed in status bar (no functional impact)
  * `time <hh:mm>` - set time displayed in status bar (no functional impact)

# 💭 About
**You can read about my motivation in this** [blog post](https://blog.thefuntasty.com/mobile-application-qa-capturing-the-evidence-a5115b0f2a4 "Mobile Application QA - Capturing the evidence"), if you made it this far in readme and you like my work, please be so kind and star this repository or leave some claps on Medium. Every appreciation empowers my motivation.
