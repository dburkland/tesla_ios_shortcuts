README
=========

### Introduction

After developing and using a [set of iOS shortcuts](https://github.com/dburkland/tesla_legacy_ios_shortcuts) for various Tesla-related functions I ran into a few issues:

  * Slow shortcut execution times, sometimes 1-2 minutes to open the frunk for example
  * Lack of advanced logic in iOS shortcuts that made dealing with certain vehicle states both slow & problematic

As a result, I have developed a new set of iOS shortcuts along with a cloud-based API service. These shortcuts are much simpler as the logic for dealing with things like vehicle state are now handled by the Cloud API service. Shortcuts now take only seconds to run regardless of what state the vehicle is in or how slow your mobile device's network connection is (as long as it is available). The Cloud API service is something I created myself in Python and host as a Google Compute Platform (GCP) Cloud Function.

### Setup

In order to import the shortcuts, you will first need to allow the import of untrusted shortcuts. This can be done by completing the steps documented [here](https://9to5mac.com/2019/08/14/allow-untrusted-shortcuts-ios-13/). When ready, you can then tap on the link next to "Download Latest Tesla Shortcuts" to download & install the shortcut downloader. With the shortcut downloader now installed, please execute it via the Shortcuts app to download each of the shortcuts in the list below. Once each shortcut has been imported into the Shortcuts app, you will then need to execute the "Generate Tesla Token" shortcut. This results in the creation of an authentication token that is used to communicate with your car. Once that is complete, you can then execute any of the other Tesla shortcuts as you wish.

### Tesla iOS Shortcut Inventory

* [Download Latest Tesla Shortcuts](https://www.icloud.com/shortcuts/200b6dc321464d308f27a803ccbb1fdc)
  * Allows you to download each of the published Tesla legacy shortcuts, right from the Shortcuts app.
  * NOTE: Anytime a new version of the Tesla legacy shortcuts is released 

* Generate Tesla Token
  * Generates an authorization token from the captured Tesla.com credentials
  * NOTE: This shortcut needs to be executed at least every 45 days since the tokens automatically expire
  * RECOMMENDATION: As long as you are on iOS 14 or greater, I would recommend you setup an automation within the shortcuts app to run this shortcut every month since the Tesla.com tokens expire after 45 days. For instructions on how to setup a monthly automation, please see the FAQs section below. 

* Actuate Frunk
  * Wakes the vehicle (if needed) and actuates the frunk

* Actuate Trunk
  * Wakes the vehicle (if needed) and actuates the trunk

* Turn On HVAC Normal
  * Wakes the vehicle (if needed), turns on the HVAC system, and sets the temperature to 67 degrees Fahrenheit

* Turn On HVAC Max
  * Wakes the vehicle (if needed), turns on the HVAC system, sets the temperature to 82 degrees Fahrenheit, and turns on the driver's seat warmer

* Turn On HVAC Max Spouse
  * Wakes the vehicle (if needed), turns on the HVAC system, sets the temperature to 82 degrees Fahrenheit, and turns on both the driver's & front passenger's seat warmers

* Turn Off HVAC
  * Wakes the vehicle (if needed) and turns off the HVAC system

* Lock Doors
  * Wakes the vehicle (if needed) and locks the doors

* Unlock Doors
  * Wakes the vehicle (if needed) and unlocks the doors

* Turn On Sentry
  * Wakes the vehicle (if needed) and turns on Sentry Mode

* Turn Off Sentry
  * Wakes the vehicle (if needed) and turns off Sentry Mode

* Vent Windows
  * Wakes the vehicle (if needed) and vents the windows

* Close Windows
  * Wakes the vehicle (if needed) and closes the windows

* Set Charge Limit
  * Wakes the vehicle (if needed) and sets the charge limit to the user-selected percentage

* Open Charge Port Door
  * Wakes the vehicle (if needed) and opens the charge port door

* Close Charge Port Door
  * Wakes the vehicle (if needed) and closes the charge port door

* Start Charging
  * Wakes the vehicle (if needed) and starts charging

* Stop Charging
  * Wakes the vehicle (if needed) and stops charging

* Honk Horn
  * Wakes the vehicle (if needed) and honks the horn

* Flash Lights
  * Wakes the vehicle (if needed) and flashes the lights

* Start Remote Drive
  * Wakes the vevhicle (if needed) and starts a remote driving session
  
### FAQs

* What can you do if you receive error messages like the one below?
  * ![](https://pbs.twimg.com/media/EHQXnncXYAEvPbZ?format=jpg&name=medium)
  * Delete the "Generate Tesla Token" shortcut and re-import it.
  * Execute the re-imported "Generate Tesla Token" shortcut, this time making sure to select "Allow" when prompted.
  * Re-run the Tesla shortcut that you originally tried to execute.
* How can I call these shortcuts using "Hey Siri"?
  * The name of the shortcut is automatically setup as the voice command phrase that Siri recognizes. 
  * If you would prefer another shortcut voice command phrase, you can simply rename the shortcut (after it is imported) in the Shortcuts app to whatever you like.
  * Once the shortcut is named appropriately, simply say "Hey Siri <Name of Shortcut>".
  * NOTE: Please keep in mind that the shortcut name must be unique from other shortcuts in your library. As an example, I tried to rename **Turn on HVAC Normal** to **Turn on Heat**, but that command is associated with HomeKit so it doesn't work. **Turn Heat On** however works perfectly fine.
* How secure are these shortcuts?
  * The authentication token that is generated by the "Generate Tesla Token" shortcut is stored in your personal Reminders App. The authentication token is only visible to apps or services that have access to your Reminders App meaning folks cannot publicly access this data by default. 
  * When a shortcut is executed, the authentication token is sent to the Cloud API service using TLS where it is then used to communicate with Tesla. The authentication token is never logged or recorded in any way, shape or form.
  * NOTE: I do NOT log or record any usage data, nor do I log or record any of the generated Tesla API tokens.
* How do I automatically run the "Generate Tesla Token" shortcut every month before my Tesla.com token expires?
  * Open the Shortcuts app on your mobile device.
  * Select the "Automation" tab at the bottom & then tap on "Create Personal Automation".
    * ![](https://www.dropbox.com/s/kvxi8z759f7np4i/IMG_0906.PNG?raw=1)
  * In the "New Automation" window tap on "Time of Day" to start the wizard.
    * ![](https://www.dropbox.com/s/zr0relwo37zursm/IMG_0793.PNG?raw=1) 
  * You should be at the screen that requires you to pick when and how often you want this automation to run. I recommend setting "Time of Day" equal to a time later in the day (like 8:00PM) and "Repeat" to "Monthly". 
    * To keep things simple, I would also suggest you set the "Starting" date to be the 1st of the month.
    * ![](https://www.dropbox.com/s/c2vk96lr4cgo4ql/IMG_0794.PNG?raw=1) 
    * Once you have selected values in the aforementioned fields, tap "Next" to proceed.
  * With the "Actions" screen now open, tap on "Add Action" to specify what you want the automation to do.
    * ![](https://www.dropbox.com/s/cf79eilkspablfd/IMG_0796.PNG?raw=1)
    * In the search field at the top, type "Shortcut" and press the "search" button in the keyboard.
    * Under "Actions", tap on "Run Shortcut".
    * Next to the word "Run", tap on the blue-colored "Shortcut" field.
    * ![](https://www.dropbox.com/s/ei3fnmtyggx4dou/IMG_0801.PNG?raw=1) 
    * Choose the "Generate Tesla Token" shortcut from the list.
    * ![](https://www.dropbox.com/s/jrm54q77wmk1j9j/IMG_0802.PNG?raw=1)
    * Press "Next" to proceed.
  * Now you should again see the "New Automation" window however this time it shows the time, frequency, and action that you defined in the previous steps.
    * Tap on the switch button next to "Ask Before Running" as we want this shortcut to automatically execute every month.
    * ![](https://www.dropbox.com/s/ydqkalhxcbjgqj7/IMG_0804.PNG?raw=1)
    * When you see a "Don't ask before running?" pop up message, make sure to select "Don't Ask" to confirm your selection.
    * ![](https://www.dropbox.com/s/0ql882kkbc408d4/IMG_0805.PNG?raw=1)
  * Tap "Done" to create your new automation.
  * NOTE: When the automation runs each month please note that it will ask for your interaction by popping up a message like the one seen in the image below:
    * ![](https://www.dropbox.com/s/0s2fudbf1tujfsg/IMG_0811.PNG?raw=1)
    * When you see this message, tap on the "Remove 1 Reminder?" pop-up.
    * Once you have tapped on the aforementioned pop-up you should then see a follow up message that asks, "Are you sure you want to remove this item?". Please select "Remove" which will delete the old Tesla.com token.
    * ![](https://www.dropbox.com/s/6qeokmucdwt142a/IMG_0812.PNG?raw=1)
    * The shortcut will then finish executing and result in the creation of a fresh Tesla.com token that will be valid for another month.
