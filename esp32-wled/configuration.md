# ESP32 and WLED Configuration

## Hardware

The project uses an ESP32-D0WDQ5 based board connected to a WS2812B LED strip.

## Firmware

**WLED:** 0.15.3

WLED provides:

- Wi-Fi connectivity
- WS2812B timing and data generation
- LED configuration
- Network-based LED control
- Standalone lighting effects for testing

## Recommended Configuration Checks

Before connecting Hyperion, verify:

- LED type is set correctly.
- LED count matches the physical strip.
- GPIO/data pin matches the actual wiring.
- Colour order matches the LEDs.
- Wi-Fi connection is stable.
- LEDs operate correctly using WLED's own effects.

These values are intentionally not hard-coded in this documentation because they depend on the actual board and wiring.

## Hyperion Control

When Hyperion is actively controlling the LEDs, Hyperion becomes the source of the changing colour data. WLED remains the firmware/controller layer on the ESP32.

Conceptually:

```
Hyperion
   ↓ network
WLED on ESP32
   ↓ data
WS2812B
```

Standalone WLED effects and Hyperion-driven output should therefore be treated as different operating modes.
