# RoboCart Extension for Microsoft MakeCode

MakeCode extension for the **RoboCart** robot car kit for micro:bit.

> This extension started as a rebranded fork of the open-source
> [pxt-zoombit](https://github.com/cytrontechnologies/pxt-zoombit) extension by
> Cytron Technologies Sdn Bhd, used here under the MIT License. All block IDs,
> the namespace, and the display name have been renamed to `robocart` /
> "ROBO:CART" for this project. See `LICENSE` for full attribution.

## Adding the Extension in MakeCode Editor

- open <https://makecode.microbit.org/>
- click on **New Project** and give your project a meaningful name
- click on **Extensions** under the gearwheel ⚙️ menu
- search for "**robocart**" or `https://github.com/<your-username>/pxt-robocart`
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

## Supported targets

- for PXT/microbit

## License

MIT — see `LICENSE`.
