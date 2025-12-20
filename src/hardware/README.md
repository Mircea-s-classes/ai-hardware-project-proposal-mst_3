# Hardware Design
# Hardware Overview – Sentinel-AI (MST_3)

## Target Platform
- NVIDIA Jetson Nano (4GB)
- JetPack 4.x / Ubuntu 18.04

## Sensors
- USB Webcam (UVC compliant)
- Microphone (USB / onboard – planned)

## Peripherals
- USB keyboard and mouse (for setup)
- HDMI display (for debugging)

## Power
- 5V / 4A DC power supply
- Barrel jack preferred for stable operation

## Connectivity
- USB 2.0/3.0 ports for camera
- Ethernet/Wi-Fi (only needed for setup)

## System Block Diagram

Camera → Jetson Nano → Face Recognition (face-api.js)
                      → Local display / overlay


# Jetson Nano Setup

## OS & SDK
- JetPack 4.6
- Ubuntu 18.04 (L4T)

## Installed Software
- Chromium Browser
- Python 3
- Git

## Notes
- All inference runs locally in the browser
- No cloud services required
- Camera access via getUserMedia()

# Camera Setup

## Camera Type
- USB UVC-compliant webcam

## Connection
- Plugged into Jetson Nano USB port

## Verification
```bash
ls /dev/video*
v4l2-ctl --list-devices

