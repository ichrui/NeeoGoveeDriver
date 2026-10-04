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

	1.	Copy the file into your meta driver's active folder:

cp goveeLight.json ~/meta/active/
pm2 restart meta

	2.	In the NEEO app: "Add Device" → search for "Govee"
	3.	Enter your Govee API key when prompted
	4.	Select your device from the list of discovered Govee devices
	5.	Done — repeat step 2–4 for each additional Govee light you want to add

Known limitation

The NEEO/meta framework defines a device's UI elements (sliders, directories) once per device type, not per individual device instance. This means the brightness slider and color picker are always visible, even for Govee devices that don't support them (e.g. simple plugs). On unsupported devices, interacting with these controls simply does nothing — the driver checks the device's reported capabilities before sending any brightness/color command, so no invalid API request is made.

Credits

Built on the meta driver framework by jac459
Driver created by: ichrui
