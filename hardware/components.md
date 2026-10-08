# Hardware Components

## Display

- 32-inch Amazon Fire TV
- Resolution: 1920 × 1080

## LED Strip

- Type: WS2812B
- Length: approximately 2.5 m
- Individually addressable RGB LEDs

The exact LED count should be recorded from the physical installation before finalising the Hyperion LED layout.

## Controller

- ESP32 development board
- WLED firmware version 0.15.3
- ESP32-D0WDQ5 based device

## Video Hardware

- HDMI splitter
- HDMI capture path connected to the Ubuntu computer

## Power

The LED strip requires an appropriate regulated 5 V supply. The ESP32 should not be used as the power source for the complete LED strip.

Power wiring should be sized for the actual LED count and maximum expected brightness. Common ground between the ESP32 and LED power system is important for reliable data signalling.

## Optional Improvements

A 5 V logic-level buffer/level shifter can improve the reliability of the data signal between the 3.3 V ESP32 output and a 5 V WS2812B installation, especially with longer data wires.
