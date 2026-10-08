# Hyperion Configuration

## Role

Hyperion.ng is the video-processing part of the Ambilight system.

It runs on Ubuntu and receives the video from the HDMI capture path. It analyses the image and generates LED colour information.

## Main Configuration Areas

### Capture

Select the HDMI capture device that receives the duplicated video signal.

### LED Layout

The Hyperion LED layout must represent the physical arrangement around the TV.

The exact LED count and positions should be taken from the current physical installation rather than assumed from the strip length.

### LED Device

Configure Hyperion to send the generated LED data to the ESP32 running WLED over the local network.

### Image Processing

Hyperion can be tuned using settings such as:

- colour calibration;
- smoothing;
- brightness limits;
- black-bar detection;
- image sampling;
- priority/source settings.

The best values depend on the display, capture device and personal preference.

## Troubleshooting

### LEDs work in WLED but change when Hyperion starts

This is expected when Hyperion begins sending LED data. Hyperion is taking control of the LED output.

Check that:

1. WLED works independently.
2. The ESP32 is connected to the same local network as Hyperion.
3. Hyperion is targeting the correct WLED device.
4. The LED count/layout matches the physical installation.
5. Only the intended Hyperion LED output is enabled.

### Hyperion has no video

Check the HDMI splitter, capture device, HDMI source and capture-device selection in Ubuntu before troubleshooting the ESP32.

### LEDs behave incorrectly

Check power, common ground, LED direction, LED count, data pin, colour order and network configuration.
