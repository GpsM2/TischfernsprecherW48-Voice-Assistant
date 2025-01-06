# TischfernsprecherW48-Voice-Assistant
Modification of a vintage "Tischfernsprecher W 48" telephone into a HomeAssistant-compatible voice assistant device

## Detailed Description
This project transforms the vintage "Tischfernsprecher W 48" telephone into a voice assistant. The device listens only when the handset is lifted, making it intuitive and eliminating the need for a wake word. Additionally, it combines the charm of a vintage telephone with modern functionality.

## Hardware Used
- [diymore ESP32 S3 DevKitC 1 N16R8 ESP32 S3 WROOM1 N16R8](https://www.amazon.de/gp/product/B0CLD4QKT1)
- [AZDelivery MAX98357A I2S 3W Mono Amplifier Class D](https://www.amazon.de/dp/B09PL7DSK5)
- [ARCELI 3PCS INMP441 Omnidirectional Microphone Module, I2S](https://www.amazon.de/dp/B0CH2TYXCZ)
- [Weewooday 6 Pieces 2W 8 Ohm Speaker](https://www.amazon.de/dp/B09MRK24PP)
- [chenyang RJ45 Stretch Spiral Cable Cat6 8P8C UTP](https://www.amazon.de/dp/B0CF2B2PCK) (at least 2 meters, 7 wires needed)

## Software Used
- ESPHome on HomeAssistant
- YAML configuration file (uploaded in this repository)

## Assembly Instructions
I removed the internal components of the telephone and replaced them with the new technology. Please refer to the uploaded images for detailed steps.

## Usage Notes
Improvements are welcome. The internal assembly could be more space-efficient, allowing the bell to be operated with an electromagnet. A custom PCB design could also be beneficial. Ensure proper strain relief for the spiral cable. The cable I used conveniently included a rope, allowing strain relief in the handset with a screw and hot glue.
