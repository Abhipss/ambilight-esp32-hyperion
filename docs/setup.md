# Setup Guide

## 1. Assemble the LED Strip

Mount the WS2812B strip around the rear edge of the TV. Keep the LED orientation consistent so the physical LED order matches the logical order configured in WLED and Hyperion.

## 2. Configure the ESP32

Install WLED 0.15.3 on the ESP32 and connect it to the local Wi-Fi network.

Configure the LED strip according to the actual hardware installation. Do not copy an LED count, GPIO number, colour order, or other hardware value from this document without checking the current WLED configuration.

## 3. Prepare the Video Path

Connect the HDMI source to the splitter.

Connect one splitter output to the TV and the other to the capture path used by the Ubuntu computer.

## 4. Configure Hyperion

Install Hyperion.ng on Ubuntu and configure:

- the video capture source;
- the LED layout;
- the number and position of LEDs;
- the WLED/ESP32 network target;
- colour calibration and smoothing as required.

The exact values depend on the final physical installation.

## 5. Test in Stages

Test the system in this order:

1. ESP32 + WLED + LED strip.
2. Network connection to the ESP32.
3. HDMI capture on Ubuntu.
4. Hyperion video preview.
5. Hyperion-to-WLED communication.
6. Full Ambilight operation.

Testing in stages makes it easier to identify whether a problem is caused by power, LEDs, networking, capture, or Hyperion configuration.
