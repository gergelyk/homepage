# UT60E Dashboard

This project is a quick yet practical PoC that verifies usability of [crystal](https://crystal-lang.org/) on aarch64 platform. It is an implementation of a driver that reads measurements from Uni-T UT60E multimeter and stores it in a [time series database](https://en.wikipedia.org/wiki/Time_series_database) from where they can be obtained for further processing or visualization.

![](https://raw.githubusercontent.com/gergelyk/ut50e-dashboard/master/docs/hardware.jpg)

Raspberry Pi on the picture measures current consumption of itself.

![](https://raw.githubusercontent.com/gergelyk/ut50e-dashboard/master/docs/grafana-current.png)

## Application

Proposed application consists of three software components:

- `ut60e` - Interface to the multimeter. Implemented in crystal and using only its standard library.
- [ticktock](https://github.com/ytyou/ticktock.git) - Efficient database implemented in C++, compatible with OpenTSDB.
- [Grafana](https://grafana.com/grafana/) - open source platform acting as a dashboard.

## Deployment Options

All the three software components are available for aarch64 and x86_64 platforms. This allows for many deployment options, where the following two seem the most practical:

![](https://raw.githubusercontent.com/gergelyk/ut50e-dashboard/master/docs/deployment.png)

- Host Deployment - It is the simplies option which can be put together quickly. All we need is the host computer and DMM. It can be used for many short at-hoc measurements. It was also usefull for development of `ut60e.cr`.
- Mixed Deployment - It is dedicated to long-term measurements where we don't want the host computer to keep working all the time. While Raspberry Pi can connect to the host over WiFi, this option is also suitable for short-range remote measurements.

Remaining part of this document assumes using **Mixed Deployment**.

## Hardware

For the purpose of this project following hardware has been used: 

- Host computer with Ubuntu Linux
- Raspberry Pi 3 Model B+
- Uni-T UT60E with original RS232 cable
- RS232-to-USB converter
