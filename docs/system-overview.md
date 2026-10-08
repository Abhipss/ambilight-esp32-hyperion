# System Overview

## Purpose

The Ambilight system adds ambient lighting behind a 32-inch 1080p Fire TV. The LEDs reproduce colours derived from the video currently being displayed.

## Signal and Data Flow

```
HDMI video
   │
   ▼
HDMI splitter ───────────────► TV
   │
   ▼
Capture path
   │
   ▼
Hyperion.ng (Ubuntu)
   │
   │ Wi-Fi / network
   ▼
ESP32 running WLED
   │
   ▼
WS2812B LED strip
```

The HDMI path carries the video signal. Hyperion performs the screen analysis, while the ESP32 is responsible for receiving the LED data and driving the addressable LED strip.

## Main Components

| Component | Role |
|---|---|
| Fire TV | Video display |
| HDMI splitter | Duplicates the HDMI signal |
| Capture path | Provides video to the Ubuntu system |
| Ubuntu PC/laptop | Runs Hyperion.ng |
| Hyperion.ng | Analyses video and generates LED colours |
| ESP32 | Network-connected LED controller |
| WLED 0.15.3 | Controls the WS2812B strip |
| WS2812B | Produces the ambient lighting |

## Operating Principle

Hyperion divides the captured screen into regions and determines representative colours. These colours are mapped to the corresponding LED positions. The resulting LED data is sent over the local network to the ESP32, where WLED updates the WS2812B strip.

The system therefore separates the work into two parts:

- **Software/video side:** capture and colour processing on Ubuntu using Hyperion.
- **Embedded/LED side:** network reception and LED control using ESP32 + WLED.
