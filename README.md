README
=========

### Introduction

After developing and using a [set of iOS shortcuts](https://github.com/dburkland/tesla_legacy_ios_shortcuts) for various Tesla-related functions I ran into a few issues:

  * Slow shortcut execution times, sometimes 1-2 minutes to open the frunk for example
  * Lack of advanced logic in iOS shortcuts that made dealing with certain vehicle states both slow & problematic

As a result, I have developed a new set of iOS shortcuts along with a cloud-based API service. These shortcuts are much simpler as the logic for dealing with things like vehicle state are now handled by the Cloud API service. Shortcuts now take only seconds to run regardless of what state the vehicle is in or how slow your mobile device's network connection is (as long as it is available). The Cloud API service is something I created myself in Python and host as a set of Amazon Web Services (AWS) Lambda Functions.

### Setup

* Prerequisites
  * To begin you will first need to download & install the [Auth app for Tesla](https://apps.apple.com/us/app/auth-app-for-tesla/id1552058613#?platform=iphone).
  * With the Auth app for Tesla now downloaded & installed, please open it. You should now see something like this:
    * ![](https://www.dropbox.com/s/ijlogo69dsywf22/IMG_2453.jpeg?raw=1)
  * Next you will need to tap on "Login with Tesla" and follow the prompts to sign into your Tesla.com account.
    * ![](https://www.dropbox.com/s/9j6cgxwy6i4twf8/IMG_2454.jpeg?raw=1)
  * If everything worked you should see something like this:
    * ![](https://www.dropbox.com/s/k1ru5y6oeanbns8/IMG_2455.jpeg?raw=1)
* Shortcut Setup
  * In order to import the shortcuts, you will first need to allow the import of untrusted shortcuts. This can be done by completing the steps documented [here](https://9to5mac.com/2019/08/14/allow-untrusted-shortcuts-ios-13/). 
  * When ready, you can then tap on the link next to "Tesla iOS Shortcuts Downloader" to download & install the shortcut downloader.
  * With the shortcut downloader now installed, please execute it via the Shortcuts app to download each of the shortcuts in the list below. Keep running the shortcut until it prompts you that it has installed all of the available Tesla iOS Shortcuts.
  * Once each shortcut has been imported into the Shortcuts app, you will then need to execute the "Create Tesla Token" shortcut. This results in the creation of the appropriate iCloud Drive directory structure & configuration file. Once that is complete, you can then execute any of the other Tesla shortcuts as you wish.

### Tesla iOS Shortcut Inventory

* [Tesla iOS Shortcuts Downloader](https://www.icloud.com/shortcuts/57df985951204a608f020d6040dd63b6)
  * Allows you to download each of the published Tesla shortcuts, right from the Shortcuts app.

* Tesla iOS Shortcuts Update Checker
  * Examines the currently installed version of Tesla iOS Shortcuts and lets you know if there is a newer version available.
  * NOTE: When a newer version of Tesla iOS Shortcuts is detected, instructions on how to download & install the latest version will be provided by this shortcut.
  * RECOMMENDATION: It is recommended to run this shortcut once a month to ensure that you have the latest version of Tesla iOS Shortcuts installed

* Create Tesla Token
  * Creates the appropriate iCloud Drive directory structure & configuration file that will be used by each of the Tesla iOS Shortcuts. Thanks to the Auth app for Tesla, authentication tokens are automatically created & refreshed. If you are not planning on using the "Start Remote Drive" shortcut you do not need to enter your password when prompted by the "Create Tesla Token" shortcut.
  * IMPORTANT NOTES:
    * If you run into any issues while executing the "Create Tesla Token" shortcut please refer to the FAQs section below.

* Open Front Trunk
  * Wakes the vehicle (if needed) and opens the front trunk.

* Close Frunk
  * Wakes the vehicle (if needed) and closes the frunk.

* Open Trunk
  * Wakes the vehicle (if needed) and opens the trunk.

* Close Trunk
  * Wakes the vehicle (if needed) and closes the trunk.

* Turn On Climate Cool
  * Wakes the vehicle (if needed), turns on the Climate Control system, and sets the temperature to 66 degrees Fahrenheit (19 degrees Celsius).

* Turn On Climate Warm
  * Wakes the vehicle (if needed), turns on the Climate Control system, and sets the temperature to 73 degrees Fahrenheit (23 degrees Celsius).

* Turn On Climate Heat
  * Wakes the vehicle (if needed), turns on the Climate Control system, sets the temperature to High, and turns on the driver's seat warmer.

* Turn On Climate Heat Passenger
  * Wakes the vehicle (if needed), turns on the Climate Control system, sets the temperature to High, and turns on both the driver's & front passenger's seat warmers.

* Turn Off Climate
  * Wakes the vehicle (if needed) and turns off the Climate Control system.

* Lock Doors
  * Wakes the vehicle (if needed) and locks the doors.

* Unlock Doors
  * Wakes the vehicle (if needed) and unlocks the doors.

* Turn On Sentry Mode
  * Wakes the vehicle (if needed) and turns on Sentry Mode.

* Turn Off Sentry Mode
  * Wakes the vehicle (if needed) and turns off Sentry Mode.

* Open Windows
  * Wakes the vehicle (if needed) and opens the windows.

* Close Windows
  * Wakes the vehicle (if needed) and closes the windows.

* Set Charge Limit
  * Wakes the vehicle (if needed) and sets the charge limit to the user-selected percentage.

* Open Charge Port Door
  * Wakes the vehicle (if needed) and opens the charge port door.

* Close Charge Port Door
  * Wakes the vehicle (if needed) and closes the charge port door.

* Start Charging
  * Wakes the vehicle (if needed) and starts charging.

* Stop Charging
  * Wakes the vehicle (if needed) and stops charging.

* Set Charging Amps
  * Wakes the vehicle (if needed) and sets the charging amps to the user-selected value.

* Enable Scheduled Charging
  * Wakes the vehicle (if needed), turns on scheduled charging, and sets the scheduled charging time to the user-selected value. 

* Disable Scheduled Charging
  * Wakes the vehicle (if needed) and turns off scheduled charging.

* Honk Horn
  * Wakes the vehicle (if needed) and honks the horn.

* Flash Lights
  * Wakes the vehicle (if needed) and flashes the lights.

* Start Remote Drive
  * Wakes the vehicle (if needed) and starts a remote driving session.

* Open Garage Door
  * Wakes the vehicle (if needed) and opens the nearest garage door.

* Close Garage Door
  * Wakes the vehicle (if needed) and closes the nearest garage door.

* Calculate Charge Time
  * Calculates the time needed to charge based on user-defined inputs.

* Store Tesla Token From TeslaFi
  * If you are a TeslaFi.com user you can record & store the current Tesla.com credentials that it is leveraging. From your mobile device simply browse to https://www.teslafi.com/tokenNew.php, tap on the "Share" icon, and then select "Store Tesla Token From TeslaFi" from the list. When you first generate your Tesla.com credentials on TeslaFi.com you need to make sure that you select the "Display Token" checkbox otherwise this shortcut will not work. 
  NOTE: Use of this shortcut replaces the need for using the "Create Tesla Token" shortcut.
  
### FAQs

* What can you do if you receive error messages like the one below?
  * ![](https://pbs.twimg.com/media/EHQXnncXYAEvPbZ?format=jpg&name=medium)
  * Try to open the Auth app for Tesla, re-login into your Tesla.com account, delete the "Create Tesla Token" shortcut, reinstall it, and then execute it again.
  * If you are still running into issues, I would then recommend verifying that:
    * Your Tesla.com account is not locked (try logging into it via https://tesla.com).
    * You are specifying your email address with the same case that matches how it exists in your Tesla.com account (the new API appears to be case sensitive).
    * You are entering the right password and MFA code (if you use MFA).
* How can I call these shortcuts using "Hey Siri"?
  * The name of the shortcut is automatically setup as the voice command phrase that Siri recognizes. 
  * If you would prefer another shortcut voice command phrase, you can simply rename the shortcut (after it is imported) in the Shortcuts app to whatever you like.
  * Once the shortcut is named appropriately, simply say "Hey Siri <Name of Shortcut>".
  * NOTE: Please keep in mind that the shortcut name must be unique from other shortcuts in your library. As an example, I tried to rename **Turn on HVAC Normal** to **Turn on Heat**, but that command is associated with HomeKit so it doesn't work. **Turn Heat On** however works perfectly fine.
* How secure are these shortcuts?
  * The authentication and refresh tokens created by the Auth app for Tesla are securely stored in your personal iCloud account. The tokens are only visible to apps or services that have access to your iCloud account meaning folks cannot publicly access this data by default. 
  * When a shortcut is executed, the authentication token is sent to the Cloud API service using TLS where it is then used to communicate with Tesla. The authentication token is never logged or recorded in any way, shape or form.
  * NOTE: I do NOT log or record any usage data, nor do I log or record any of the created Tesla API tokens.
