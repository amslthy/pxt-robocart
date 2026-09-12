# 🚗 RoboCart Extension for Microsoft MakeCode

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Target: micro:bit](https://img.shields.io/badge/target-micro%3Abit-blue.svg)](https://makecode.microbit.org/)
[![MakeCode Extension](https://img.shields.io/badge/MakeCode-Extension-orange.svg)](https://makecode.microbit.org/extensions)

MakeCode extension for the **RoboCart** robot car kit for micro:bit — control
DC motors, headlights, a line sensor, and an ultrasonic sensor with simple
drag-and-drop blocks.

<p align="center">
  <img src="icon.png" alt="RoboCart logo" width="160"/>
</p>

> **Attribution:** This extension started as a rebranded fork of the
> open-source [pxt-zoombit](https://github.com/cytrontechnologies/pxt-zoombit)
> extension by Cytron Technologies Sdn Bhd, used here under the MIT License.
> All block IDs, the namespace, and the display name have been renamed to
> `robocart` / "ROBO:CART" for this project. Motor control is powered by the
> [pxt-rekabit](https://github.com/cytrontechnologies/pxt-rekabit) driver.
> See [`LICENSE`](./LICENSE) for full details.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Examples](#examples)
- [Pinout](#pinout)
- [Supported Targets](#supported-targets)
- [License](#license)

## Features

| Block Group | What it does |
|---|---|
| 🔦 Headlights | Turn on/off or toggle left, right, or both headlights |
| ⚙️ DC Motors | Move forward/backward, turn left/right, brake, or set each motor's speed independently |
| 📏 Maker Line | Detect line position (far left → far right) with a single sensor |
| 📡 Ultrasonic | Read distance in centimeters for obstacle detection |

## Installation

- open <https://makecode.microbit.org/>
- click on **New Project** and give your project a meaningful name
- click on **Extensions** under the gearwheel ⚙️ menu
- search for "**robocart**" or `https://github.com/amslthy/pxt-robocart`
- click on the RoboCart card to install the extension

## Examples

### Headlights

Turn on headlights when button A is pressed, turn off when button B is pressed.

```blocks
input.onButtonPressed(Button.A, function () {
    robocart.setHeadlight(HeadlightChannel.All, robocart.digitalStatePicker(DigitalIoState.On))
})
input.onButtonPressed(Button.B, function () {
    robocart.setHeadlight(HeadlightChannel.All, robocart.digitalStatePicker(DigitalIoState.Off))
})
```

### DC Motors

Move robot forward at speed 128 when button A is pressed, brake/stop the robot when button B is pressed.

```blocks
input.onButtonPressed(Button.A, function () {
    robocart.move(MotorDirection.Forward, 128)
})
input.onButtonPressed(Button.B, function () {
    robocart.brake()
})
```

### Maker Line Sensor

Show line position on the LED matrix display.

```blocks
basic.forever(function () {
    if (robocart.isLineDetectedOn(LinePosition.Center)) {
        basic.showIcon(IconNames.Yes)
    } else {
        basic.clearScreen()
    }
})
```

### Ultrasonic Sensor

Show *Heart* when an object is detected less than 15cm away from the ultrasonic sensor, otherwise show *Small Heart*.

```blocks
basic.forever(function () {
    if (robocart.readUltrasonic() < 15) {
        basic.showIcon(IconNames.Heart)
    } else {
        basic.showIcon(IconNames.SmallHeart)
    }
})
```

## Pinout

| Component | Pin(s) |
|---|---|
| Left headlight | P13 |
| Right headlight | P15 |
| Maker Line sensor | P1 |
| Ultrasonic — Trig | P2 |
| Ultrasonic — Echo | P12 |
| Left / Right motor | via `pxt-rekabit` (M1 / M2) |

> Update the pin constants at the top of `main.ts` if your wiring differs.

## Supported Targets

- ✅ PXT / micro:bit

## Contributing

Issues and pull requests are welcome. Please open an issue first to discuss
any major changes.

## License

Released under the [MIT License](./LICENSE). Portions of this code are based
on Cytron Technologies' `pxt-zoombit` (MIT) — see the attribution note above.
