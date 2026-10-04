Govee Light – meta Driver for NEEO

A driver for the meta remote framework by jac459 to control Govee smart lights through the official Govee Cloud API (openapi.api.govee.com).

Developed and tested with a Govee H607C LED strip, but works with any Govee light device exposed through the Govee Developer API — no driver changes needed per model.

Features

	•	Power on/off
	•	Brightness control (if supported by the device)
	•	Color picker with 10 preset colors (if supported by the device)
	•	Automatic device discovery — lists all your Govee devices during setup, no need to manually look up device IDs
	•	Capability-aware: devices that don't support brightness or color simply ignore those controls instead of sending failing API requests

Requirements

	•	A Govee API key. Get one free in the Govee Home app: Profile → About Us → Apply for API Key (usually arrives within minutes by email)
	•	A Govee device registered to your Govee account (added via the Govee Home app first)

Files

File	Purpose
goveeLight.json	Generic Govee light driver — works for any Govee light on your account
Icons/GoveeLight.png	Driver icon for use in the Driver Library (IconLocation)

Installation

There are two ways to install this driver:

Variant 1: Manual installation

	1.	Copy the file into your meta driver's active folder:

cp goveeLight.json ~/meta/active/
pm2 restart meta

	2.	In the NEEO app: "Add Device" → search for "Govee"
	3.	Enter your Govee API key when prompted
	4.	Select your device from the list of discovered Govee devices
	5.	Done — repeat step 2–4 for each additional Govee light you want to add

Variant 2: Via the Driver Library (metaCore)

If you have the metaCore driver installed, you can install "Govee Light" directly from the NEEO app without touching the file system:

	1.	Open the metaCore "Driver Library" shortcut on your remote/app
	2.	Select "Update Driver Library" to fetch the latest list
	3.	Find "Govee Light" in the list and select it to activate
	4.	Restart meta (metaCore can do this for you from the "Danger Zone" menu)
	5.	Continue with steps 2–5 from Variant 1 above (add the device in the NEEO app)

Usage

Make sure to use POWER ON and POWER OFF when launching and closing your NEEO recipe

POWER ON and POWER OFF are the events the meta driver uses to start and stop listening to your Govee light's state. If you don't include them in your recipe, state changes (brightness, color, on/off) won't update live in the NEEO app.

If you have several Govee lights combined under one device/recipe, you need to call POWER ON and POWER OFF individually for each one.

Known limitation

The NEEO/meta framework defines a device's UI elements (sliders, directories) once per device type, not per individual device instance. This means the brightness slider and color picker are always visible, even for Govee devices that don't support them (e.g. simple plugs). On unsupported devices, interacting with these controls simply does nothing — the driver checks the device's reported capabilities before sending any brightness/color command, so no invalid API request is made.

Credits

Built on the meta driver framework by jac459.
Driver created by: ichrui