# RTIC MicKey Mouse

<p align="right">
<a href="https://github.com/gergelyk/retro-clock"><img src="/assets/github.svg"/></a>
</p>

Prototype of a clock combined with meteo station.

![](https://raw.githubusercontent.com/gergelyk/retro-clock/main/docs/img/overview.png)

## Features

- Local Time
- Word Time
- Current Weather
- Weather Forecast
- Adaptive Illumination
- Configuration Over WiFi
- Simple Controls
- Failure Resistance
- Data Safety

## Implementation

Project consists of two parts:

1. Embedded
  - Configuration UI, build in Leptos
  - Firmware, build on top of esp-idf
  - Runs on Espressif ESP32-S3

2. Cloud-based
  - Frontend, build in Leptos
  - Backend, built on top of Spin Framework
  - Deployed to the Fermion Cloud

## More Details

- [Repository](https://github.com/gergelyk/retro-clock)
- [Presentation](https://www.youtube.com/watch?v=yR7irQRpGIg)
- [Slides] (https://filedn.com/ls8U70bX0lASS65WlPE8h3j/PERMALINKS/retro-clock-slides/index.html)
