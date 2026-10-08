# Ambilight with Hyperion, ESP32, WLED and WS2812B

A DIY Ambilight system built around an ESP32 running WLED, a WS2812B LED strip, and Hyperion running on Ubuntu.

## Overview

This project extends the visual experience of a 32-inch 1080p Fire TV by matching the LED colours behind the display to the colours detected from the video.

The system uses HDMI video capture and software processing rather than directly modifying the TV.

## System Architecture

```
Video Source
    │
    ▼
HDMI Splitter
    ├──────────────► TV / Display
    │
    ▼
HDMI Capture
    │
    ▼
Hyperion.ng on Ubuntu
    │
    │ Wi-Fi
    ▼
ESP32
    │
    ▼
WLED
    │
    ▼
WS2812B LED Strip
    │
    ▼
Ambient light behind TV
```

## Hardware

- 32-inch 1080p Amazon Fire TV
- ESP32 development board
- WS2812B addressable RGB LED strip
- Approximately 2.5 m LED strip
- HDMI splitter
- Ubuntu laptop/PC running Hyperion.ng
- 5 V power supply / suitable regulated supply for the LED strip
- Common ground between the LED power system and ESP32

## Software

### WLED

WLED runs on the ESP32 and controls the WS2812B LEDs.

The ESP32 used in the project is an ESP32-D0WDQ5 based board.

WLED provides the LED control interface and accepts colour data sent over the network.

### Hyperion.ng

Hyperion.ng runs on Ubuntu and performs the screen-colour analysis.

It receives the video from the HDMI capture path, calculates representative colours for different regions of the screen, and sends the resulting LED data to WLED over Wi-Fi.

## How It Works

1. The video source produces an HDMI signal.
2. The HDMI splitter duplicates the signal.
3. One HDMI output goes to the TV.
4. The other output is connected to the capture path connected to the Ubuntu system.
5. Hyperion analyses the captured video.
6. Hyperion calculates the colours corresponding to different areas around the screen.
7. The colour information is transmitted over Wi-Fi.
8. The ESP32 receives the data through WLED.
9. WLED updates the individual WS2812B LEDs.
10. The LEDs reproduce the colours around the back of the TV, creating the Ambilight effect.

## Current Configuration

- Display: 32-inch 1080p Fire TV
- LED strip: WS2812B
- LED strip length: approximately 2.5 m
- Controller: ESP32
- LED firmware: WLED 0.15.3
- Hyperion host: Ubuntu
- Communication: Wi-Fi
- LED control: WLED
- Video processing: Hyperion.ng

## Power

The WS2812B strip requires a stable 5 V supply. The LED strip should not be powered directly from the ESP32.

The ESP32 and LED system should have a suitable common ground so that the LED data signal has a reliable reference.

A dedicated regulated 5 V supply is preferred for the LED strip because the current requirement increases with the number and brightness of LEDs.

## Important Design Considerations

### HDMI Capture

The Ambilight effect depends on Hyperion receiving the same video that is displayed on the TV. Therefore, an HDMI splitter and capture device are useful when the display itself does not provide a suitable video capture interface.

### Wi-Fi

The ESP32 communicates with Hyperion over the local network. This avoids running a long data cable from the Ubuntu computer to the TV.

### LED Data

WS2812B LEDs use a single-wire digital data signal. WLED generates the appropriate timing and colour data for the complete strip.

### Power Injection

For longer LED strips, voltage drop can become significant. The approximately 2.5 m strip used here should still be designed with appropriate power wiring, especially when high brightness or many LEDs are used.

## Problems Encountered

During development, WLED control worked correctly when tested independently.

When Hyperion was active, the LED behaviour changed because Hyperion was sending its own LED data to the ESP32. This means WLED's normal effects and Hyperion's external LED control should not be treated as two independent controllers at the same time.

The practical operating mode is:

```
Hyperion → Network → WLED/ESP32 → WS2812B
```

rather than manually changing WLED effects while Hyperion is actively controlling the LEDs.

## Future Improvements

- Add a dedicated HDMI capture card if not already integrated into the final setup.
- Improve cable management and LED mounting behind the TV.
- Add proper power injection where required.
- Add a level shifter for a more robust 3.3 V ESP32-to-5 V LED data interface.
- Add a suitable logic-level buffer such as a 74-series 5 V buffer if required.
- Create a permanent enclosure for the ESP32 and power connections.
- Experiment with microphone-based reactive lighting as a separate WLED mode.
- Improve Hyperion colour calibration and LED layout configuration.

## Project Goal

The goal of this project is to build a low-cost, network-controlled Ambilight system using readily available hardware and open-source software.

The project demonstrates the integration of:

- Addressable RGB LEDs
- ESP32 embedded control
- WLED firmware
- Wi-Fi communication
- HDMI video distribution
- Video capture
- Real-time image/colour processing
- Hyperion.ng
- Hardware and software integration

## Status

**Working prototype**

The ESP32 + WLED + WS2812B lighting system works, and Hyperion can control the LEDs through the network. The project can be further improved with dedicated capture hardware, better power distribution, and a more permanent physical installation.

## Author

**Abhinand P S**

MSc Electronics  
Cochin University of Science and Technology (CUSAT)

## License

This project documentation is provided for educational and personal use.