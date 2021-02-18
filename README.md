# homebridge-visonic-powerlink3

This [Homebridge](https://github.com/nfarina/homebridge) plugin allows [Visonic](http://visonic.com) security systems, which have the optional [PowerLink3](https://www.visonic.com/Products/Wireless-Property-Protection/powerlink3-communication-modules) module inside, to be controlled using [Apple HomeKit](https://developer.apple.com/homekit/) (e.g. [in the Home app on iOS, and via Siri](https://www.apple.com/uk/ios/home/))

[Homebridge](https://github.com/nfarina/homebridge) acts as a bridge between HomeKit (on your Apple devices) and (non-HomeKit-supporting) accessories you have. If you don't already have a computer that can be left running Homebridge continuously at home, [you could set up Homebridge on a Raspberry Pi](https://github.com/nfarina/homebridge/wiki/Running-HomeBridge-on-a-Raspberry-Pi).

<br><a href="https://www.buymeacoffee.com/tkleijkers" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-black.png" width="150px" height="35px" alt="Buy Me A Coffee" style="height: 35px !important;width: 150px !important;" ></a>

## Install

1. Install Homebridge by following its [installation steps](https://github.com/nfarina/homebridge#installation)
2. Install this plugin: `npm install -g homebridge-visonic-powerlink3`
3. Edit your Homebridge `config.json` file (`~/.homebridge/config.json` on macOS and Linux), adding your security system to `accessories` – see the sample below

## Configuration

**Configuration sample:**

 ```javascript
	"accessories": [

		{
			"accessory": "PowerLink3",
			"name": "Security System",

			"host": "visonic.tycomonitor.com",
			"userCode": "your-user-code",
			"appType": "com.visonic.PowerMaxApp",
			"userId": "your-random-guid",
			"panelWebName": "your-panel-web-name",
			"userEmail": "youremail@domain.com",
			"userPassword": "your-secret-password"
		}
	]
```

**Required parameters:**

* `host` **string** – The IP address, or hostname, of the PowerLink3 server

* `userCode` **string** – The pin code you use to disarm or arm the system

* `appType` **string** – Default: com.visonic.PowerMaxApp

* `userId` **string** – A newly generated GUID

* `panelWebName` **string** – The panel web name as used in the Visonic GO app

* `debug` optional **boolean** – Turns on extensive logging, to help debug issues, when set to `true` (default: `false`)

* `userEmail` **string** - Your e-mail to login to Visonic

* `userPassword` **string** - Your password to login to Visonic

**Optional parameters:**

* `pollForChanges` **boolean** – Turns on continued polling of the system state: if the system status gets changed externally (e.g. via a physical keypad), HomeKit will still get notified of the change (default: `true`)

* `pollingInterval` **number** – How long, in seconds, to wait between each poll. Each poll seems quite intensive on the PowerLink2; a value of 10 seconds or greater is recommended to avoid it going unresponsive & restarting. (default: `30`)

* `debug` **boolean** – Turns on extensive logging, to help debug issues, when set to `true` (default: `false`)
