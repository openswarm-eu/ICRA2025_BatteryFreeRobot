# ICRA2025_Battery-Free Robot CapBot 

## Abstract

> Swarm robotics focuses on designing and coordinating large groups of relatively simple robots to perform tasks in a decentralised and collective manner.
> The swarm provides a resilient and flexible solution for many applications.
> However, contemporary swarm robots have a significant power problem in that secondary (i.e. rechargeable) batteries are slow to charge and offer lifetimes of only a few years, increasing maintenance costs and pollution due to battery replacement.
> We imagine a different future, wherein battery-free robots powered by supercapacitors can be recharged in seconds, offer long-life autonomous operation and can rapidly pass charge between one another using trophallaxis.
> In pursuit of this vision, we contribute the _CapBot_, a battery-free swarm robot equipped with Mecanum wheels, a Cortex-M4F application processor and Bluetooth Low Energy networking.
> CapBot  fully recharges in 16 s, offers 51 min of autonomous operation at top speed, and can transfer up to 50% of its available charge to a peer via trophallaxis in under 20 s.
> It is fully open-source: all software and hardware sources are available in this repository.

## Artefacts

### Hardware

CapBot's hardware is designed using KiCad, the design files are provided under [Hardware_Design](./Hardware_Design).

### Software

The [Software_Design](./Software_Design) folder contains an example using the CapBot Zephyr API.
The library itself is hosted at our [GitLab instance](https://gitlab.kuleuven.be/distrinet/taskforces/nes/capbot) and is included in this example using git submodules.

# CapBot ICRA demo

Fetch submodules:
```sh
git submodule update --init
```
Open workspace in [Visual Studio Code](https://code.visualstudio.com/):
```sh
code Software_Design
```
Make sure that the nRF Connect extension is installed according to the instructions at [Nordic's DevAcademy](https://academy.nordicsemi.com/courses/nrf-connect-sdk-fundamentals/lessons/lesson-1-nrf-connect-sdk-introduction/topic/exercise-1-1/)
Now, you should be able to open an nRF Connect terminal in Visual Studio Code. 
Next, execute [west](https://docs.nordicsemi.com/bundle/ncs-latest/page/zephyr/develop/west/index.html):
```sh
west build --build-dir build --board freebot-nrf52840 . -- -DBOARD_ROOT=.
```
This builds the demo project and creates a binary at `build/zephyr/zephyr.elf`.
[PyOCD](https://pyocd.io/) can then be used to flash the binary to the robot:
```sh
pyocd load -t nrf52840 build/zephyr/zephyr.hex
```

