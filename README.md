# esphome-scoreboard
An ESPHome project for controlling a relay-based scoreboard with timer.

## summary
A controller for a large scoreboard using seven-segment displays made with 12V LED strips. Each strip is controlled with a relay. Each relay is controlled with 3V3 IO supplied by an I2C IO expander. An ESP32 running ESPHome connects to Wi-Fi to present a local web UI for controlling the outputs to the IO expander. Authentication for the web server prevents unwanted access.

The home/away segment layout is:
 _      _____       \
| |  _ |__A__| _    \
| | | |       | |   \
| | |F|       |B|   \
|T| |_| _____ |_|   \
|E|  _ |__G__| _    \
|N| | |       | |   \
| | |E|       |C|   \
| | |_| _____ |_|   \
|_|    |__D__|      \

The timer segment layout is:
     TENS          ONES         \
    _____          _____        \
 _ |__A__| _    _ |__a__| _     \
| |       | |  | |       | |    \
|F|       |B|  |f|       |b|    \
|_| _____ |_|  |_| _____ |_|    \
 _ |__G__| _    _ |__g__| _     \
| |       | |  | |       | |    \
|E|       |C|  |e|       |c|    \
|_| _____ |_|  |_| _____ |_|    \
   |__D__|        |__d__|       \

## materials
* Any esp32 with Wi-Fi
* PCA9535-based 32-bit I/O expander (https://core-electronics.com.au/io-zero-32-1.html)
* 2x 3V3 capable 16-channel relay module (https://www.umart.com.au/product/sainsmart-16-channel-relay-module-60452)

## building
* Install ESPHome command line
* Add a secrets.yaml file containing the following:
```
#  Wifi
WifiSsid: "MySSID"
WifiPassword: "MySSIDPwd"

# AP Fallback
APSsid: "Fallback Hotspot"
APPassword: "FallbackPwd"

# Web Server
WebUser: "MyUser"
WebPassword: "MyUserPwd"

# OTA password
OTAPassword: "OTAPwd"
```
* Build and flash to device with `esphome run scoreboard`