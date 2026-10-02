# ESP32-S3 Button and Two Opposite LEDs

## Description
A push button controls two LEDs on an ESP32-S3. LED1 turns ON while the
button is pressed. LED2 shows the opposite state, so it is ON when the
button is released.

## Hardware used
- ESP32-S3 dev board
- 1 push button
- 2 LEDs
- 2 x 220 Ω resistors
- Breadboard and jumper wires

## Wiring (GPIO connections)
| Part | Connection |
|---|---|
| Button leg 1 | GPIO 4 |
| Button leg 2 | GND |
| LED1 (status) | GPIO 5 through 220 Ω resistor, other leg to GND |
| LED2 (opposite) | GPIO 6 through 220 Ω resistor, other leg to GND |

![Circuit photo](circuit.png)

## Observation table
| Button state | GPIO 4 reads | LED1 (GPIO 5) | LED2 (GPIO 6) |
|---|---|---|---|
| Released | HIGH | OFF | ON |
| Pressed | LOW | ON | OFF |

## Reset test
After pressing the RST/EN button with the push button released,
LED1 was OFF and LED2 was ON, as expected.

## What HIGH and LOW mean for the button
The button connects GPIO 4 to GND, and the pin uses the internal pull-up
resistor (`INPUT_PULLUP`). When the button is released, the pull-up holds
the pin at 3.3 V, so it reads HIGH. When the button is pressed, the pin is
connected to GND (0 V), so it reads LOW. This is called active-low: LOW
means pressed. The pull-up keeps the input stable when released, so it
does not change randomly.

## Code
See [button_led.ino](button_led.ino).

## Demo video
[Watch the demo](PASTE-YOUR-VIDEO-LINK-HERE)
