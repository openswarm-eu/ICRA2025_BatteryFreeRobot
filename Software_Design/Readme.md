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
