# Custom Button Labels for Elite Dangerous

<img src="docs\images\Settings Compared.png" alt="Settings Compared" style="zoom:50%;" />

What sorcery is this? None really, I just populated a couple of XML files in my Bindings folder according to Frontier's documentation. You can freely name all the buttons and axes, for example to distinguish the throttle from the stick as above, and a variety of icons are available. The best part is that the names are shown not just in the Settings panels, but everywhere in-game:

### Pre-flight

<img src="docs/images/Pre-Flight.png" alt="Pre-Flight" style="zoom:75%;" />

### Standard Cam

<img src="docs/images/Standard Cam.png" alt="Standard Cam" style="zoom:75%;" />

### Free Cam

<img src="docs/images/Free Cam.png" alt="Free Cam" style="zoom:75%;" />

### Full Spectrum Scanner

<img src="docs/images/FSS.png" alt="FSS" style="zoom:75%;" />

### FSS Help Screen

<img src="docs/images/FSS Help.png" alt="FSS Help" style="zoom:75%;" />

## Getting started

First navigate to the game's `ControlSchemes`  folder. By default this is at `%LocalAppData%\Frontier_Developments\Products\elite-dangerous-odyssey-64\ControlSchemes`. Steam users may find the file at `[your Steam library location]\steamapps\common\Elite Dangerous\Products\elite-dangerous-odyssey-64\ControlSchemes`.

Inside you will find a folder called `DeviceButtonMaps` and in it is a `Readme.txt` file plus a couple of sample button map files. Note however that we don't want to change anything in here because any changes will be clobbered by the next game update. Still the readme is very useful as it lists all the icons that are currently available.

Instead you want to go to your Bindings folder, which is at `%LocalAppData%\Frontier Developments\Elite Dangerous\Options\Bindings`. If you have been playing for any length of time you probably know the importance of keeping a backup of this folder. In this Git repo, go to `.\files\INTO Bindings` and copy the `DeviceButtonMaps` folder from there to your own Bindings folder. That's it, all done. 

At the time of writing the folder includes `Generic.buttonMap`, which has every button and axis defined, so as to act as a starting point for your own customization, plus complete button maps for the following devices (in alphabetical order):
- CH Products Pro Throttle USB
- Footcontrol USB
- Thrustmaster T.16000M
- Thrustmaster TWCS
- TurtleBeach VelocityOne FlightStick
- VKB Gladiator NXT EVO Space Combat Grip Premium (Left)
- VKB Gladiator NXT Premium Right
- VKB Gladiator NXT EVO Space Combat Grip Premium (Left)
- VKB Gladiator NXT EVO Space Combat Grip Premium (Right)
- VKB Gladiator NXT EVO Space Combat Grip Premium OmniThrottle (Left)
- VKB Gladiator NXT EVO Space Combat Grip Premium OmniThrottle (Right)
- VKB Gladiator NXT EVO Space Combat Grip Premium (Right) + GNX FSM-GA module
- VKB Gunfighter Space Combat Grip Premium (Right)
- VKB STECS Modern Throttle System Standard
- VKB STECS Regular Throttle System Mini Plus (Left)
- VKB STECS Space Throttle Grip Max (Left)
- VKB STECS Space Throttle Grip Mini (Left)
- VKB STECS Space Throttle Grip Mini (Right)
- VKB STECS Space Throttle Grip Mini Plus (Left)
- VKB STECS Space Throttle Grip Mini Plus (Right)
- VKB STECS Space Throttle Grip Standard (Left)
- VKB STECS Space Throttle Grip Standard (Right)
- VPC Throttle MT-50CM3 (Left)
- VPC WarBRD Constellation Alpha Prime (Right)

As Frontier's readme notes, you can edit and save these button maps while the game is running to experiment with how different names and icons look. Just go into Options -> Controls and the game will re-read them.

## Creating your own button maps

Before you can create custom button labels for your devices, you need to identify the name of the device you want to map. If you don't know what that is, go into your Bindings folder at `%LocalAppData%\Frontier Developments\Elite Dangerous\Options\Bindings` and open your current `.binds` files in a text editor. Look for sections that start with `Device=` and note the value(s). These are your device names. If you don't recognize the device name, the device may be identified using its VID and PID (as discussed below).

To create your own button labels, start by copying `Generic.buttonMap` to a new file. Change the name of the file to match the device name for the controller you want to customize (e.g. `T16000MTHROTTLE.buttonMap` for device name `T16000MTHROTTLE`). 

Open the file and edit the names and icons as you wish. You can refer to the `Readme.txt` in the `ControlSchemes\DeviceButtonMaps` folder for a list of available icons. Save your changes.

Update: CMDR NutBall has very kindly compiled a preview sheet of all the available icons [here](https://cmdr-nutball.github.io/Elite-Dangerous-buttonmap-Icons/).

We very much welcome contributions extending our device coverage. A GitHub pull request is the simplest way.

## Troubleshooting
Elite Dangerous expects valid XML in the buttonMap files, and will reject buttonMaps that do not fully parse without any error messages. If you have any trouble it is recommended that you run your file through a visual XML parser, such as [this one](https://jsonformatter.org/xml-parser), to check for issues.

## Forum Thread
GitHub is great for change management but not so great for discussion. If preferred, there is a [thread on Frontier's Forums](https://forums.frontier.co.uk/threads/custom-button-labels-for-elite-dangerous.641113/).

## Bonus Content: Named devices versus VID and PID

Every USB device has a Vendor ID (VID) and Product ID (PID) - these are 4 hexadecimal digits each. Your `.binds` files may identify your control using its VID and PID. 

You can create your button labels using that same VID and PID, Hence `231D0200.buttonMap` for my VKB Gladiator NXT Premium Right stick which has VID 231D and PID 0200.

In their readme, Frontier advise making sure that your device is listed in the `ControlSchemes\DeviceMappings.xml` file but editing this file can have undesirable effects:

1. Your `.binds` file will start using that name instead of the VID and PID, meaning that sites like [EDRefCard](https://edrefcard.info/) won't know what to do with it.
2. The next game update will clobber your changes (I have confirmed this personally). If you forget to reinstate your edits before  launching the game, it won't recognize the custom name on your `.binds` file, won't be able to load it, and may even clobber it too.

It's up to you but personally I like to leave the game's Products directory well alone and put up with the slightly ugly alternative VID+PID naming convention.

Enjoy!

### Postscript about the GNX button map

A *very* thorough reader might notice that my `231D0200.buttonMap` has an unexpected entry at the end:
```xml
	<Joy_31>GNX C1 Long Press</Joy_31>
```
This is indeed a customization that I made to my own stick using VKB's software -- I configured a long press on C1 as a virtual button 31 which I use to toggle my TrackIR. You can ignore this unless you have also used VKB's software in this way, in which case I'm sure you know what you're doing.
