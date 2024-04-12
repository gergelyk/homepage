# Temperature & Humidity Monitor

<p align="right">
<a href="https://github.com/gergelyk/mpy-temp-humi"><img src="/assets/github.svg"/></a>
</p>

Damn simple application implemented in MicroPython, dedicated for ESP8266 platforms.

<p align="center">
<img src="https://raw.githubusercontent.com/gergelyk/mpy-temp-humi/master/docs/device.jpg">
</p>

<p align="center">
<img src="https://raw.githubusercontent.com/gergelyk/mpy-temp-humi/master/docs/ui.png">
</p>

## Features

- Measures humidity & temperature
- Provides current, max & min readings on the display
- Provides historical readings in form of a graph
- Doesn't need internet connection
- Three time range configurations: 5 min, 1 h, 24 h
- Three display modes: light, dark, night
- Three WiFi modes: disabled, access-point, station

![](https://raw.githubusercontent.com/gergelyk/mpy-temp-humi/master/docs/wifi_modes.png)

## Usage

Press RESET button to reset device. Press DISP button to switch display mode.

By default device starts in access-point WiFi mode. In this mode, you can connect your computer/smartfon directly to ESP8266. Follow instructions on the screen.

In order to disable WiFi, or switch to station mode, open your web browser and select WiFi Setup. Provide SSID and password. After reset, ESP8266 will connect to your switch/router. It will be accessible under IP displayed on the screen.

Hold DISP button any time to reset WiFi settings.

## Design Decisions

- Frontend has been built using minimalistic libraries ([chota](https://jenil.github.io/chota/), [uplot](https://github.com/leeoniya/uPlot)) in order to fit it into persistent memory and be served efficiently.
- In order to save resources in ESP8266, frontend has been built as a set of static HTML files and is rendered entirely on the client side.
- Final source code is compiled to .mpy files to boost startup time and to save memory.
- Data type optimizations (`array`, `const`) and Python generators have been employed to save memory in ESP8266.
- Viper code and Native code emiters didn't bring much benefits and havn't been used in this application.
- Dedicated web framework (*mlask*) has been developed to meet aforementioned criteria.

## More Details

[Here...](https://github.com/gergelyk/mpy-temp-humi)
