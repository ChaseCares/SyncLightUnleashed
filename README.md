# Synclight Adaptation for ESPHome

> [!IMPORTANT]
> This is a work in progress.

## This project is not associated with Synclight CA

The [Long Distance Friendship Hearts](https://synclight.ca/products/long-distance-friendship-hearts) is a ESP powered LED light, it features:

[Archive URL](https://web.archive.org/web/20240220132650/https://synclight.ca/products/long-distance-friendship-hearts)

Images:

* [Front](./img/IMG_0940.jpg)
* [Back](./img/IMG_0940.jpg)

Characteristics:

* ESP_8266 ([ESP_12F](https://www.waveshare.com/esp-12f.htm))
* 21 NeoPixels (WS2811*)
* Physical reset button on face
* Capacity touch button on bank
* Red PCB in the shape of a heart
* Made in canada with parts from China

Note: The exact model of NeoPixel isn't confirmed, other than what is currently working with ESPHome and the device.

### This firmware is not compatible with the stock firmware provided by Synclight CA and they may not provide support if you choose to utilize this information

Synclight CA would most likely provide the code/firmware if you wanted to revert back to the stock firmware. I do not believe they are obligated to and they would be providing this assistance at their own discretion. Please be polite and understanding if they decide to not provide support.

If you need any assistance please open and issue here and I will do what I can to assist you.

## Getting Started

### Local Installation with ESPHome

Adding the device to ESPHome is very easy, just click `+ New Device` and add the device as you would with any other ESP. If it's not recognized on the first try press the reset button on the LED side of the device. After the device has been added to ESPHome you can use the [example](./example.yaml) yaml provided to set up the device.

### Remote Installation

The point of the device is to synchronize them in remote locations, so here are the instructions you could give to someone, to convert their device without a native installation of ESPHome.

You will need to create a new device(s) that we can use to configure and compile the firmware needed for the device, once the device has been configured click "install" then "manual download". This is a bin file that you will give to the other party(s) to install on their devices.

#### Information

Remote Users should receive:

* A bin file
* Name of the device
* Wi-Fi AP password
* Web Username
* Web Password

#### Instructions

##### Step One

The following steps are only required on the initial installation of the device, if you've already completed these steps previously you can skip to [Step Two](#step-one).

* Navigate to <https://esphome.io/projects/> (needs to be on chrome)
* Choose "Empty ESPHome device"
* Plug the the device in to the computer
* Click "Connect"
* Choose the device from the drop down (there should only be one)
* If it doesn't connect press the small button on the LED side of the device and try again
* When prompted click "Install ESPHome Web"
* Then click "Install"
* Should see "connecting -> erasing -> installing -> Installation complete!" then click next
* Add Wi-Fi credentials, click "connect"
* Click "visit device". Remember the ip, should be something like "10.xx.xx.xx" or "192.168.x.x"
* Under "OTA Update", click "Choose File", select "<Name_of_device>.bin" (probably in downloads) then click open, then "Update". Should see "Update Successful!"

##### Step Two

> [!IMPORTANT]
> Only give your Wi-Fi info to people you trust. This information could potentially reveal your physical location, as well as the devices on your local network. Exercise caution.

These steps are required if the Wi-Fi information is not baked into the firmware or if a device is unable to connect to the Wi-Fi for any reason.

* Search for the Wi-Fi named "Synclight Hotspot", and connect to it with the password provided to you.
* After connecting, navigate to "192.168.4.1"
* Enter the username and password provided to you
* Now connect the device to your Wi-Fi

If all goes well the device should be accessible via the IP or <device_name>.local and syncing they're light patterns.

## TODO

* When available, integrate the WireGuard component <https://github.com/droscy/esp_wireguard/tree/draft/esp8266/5>
* Add more effects <https://esphome.io/components/light/#light-effects>
* Utilized less lambda
* Refine weird back button

## Motivation

At the time this repo was created there was an outage with the MQTT server that Synclight CA utilizes, rendering the devices nonfunctional. So I wanted to create my own implementation to get the devices up and running again.

## Works Cited

<https://esphome.io> the information provided was extremely valuable in getting the device working.

<!-- long_distance_friendship_hearts -->
