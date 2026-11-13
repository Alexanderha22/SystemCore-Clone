# SystemCore Clone

A simple project to run the SystemCore image on a Raspberry Pi with a CAN Hat

## Required Software

The following software is required to create, flash, and use the SystemCore image.

### Raspberry Pi Imager

Used to flash the operating system image to a microSD card.

-   <https://www.raspberrypi.com/software/>

### WPILib alpha

Required if you are using the latest WPILib beta release. Tested with alpha 7, but should work with alpha 8

-   <https://github.com/wpilibsuite/allwpilib/releases#release-v2027.0.0-alpha-8>

-   <https://github.com/wpilibsuite/allwpilib/releases#release-v2027.0.0-alpha-7>

### SystemCore Base Image

This is the base os image used Tested with beta 15

-   <https://github.com/LimelightVision/systemcore-os-public/releases>

### Software for Motor Controllers

The following software is required to run to install the motor controller firmware for their 2027 libraries

Phoenix Tuner X Preview (If using phoenix library)

-   <https://apps.microsoft.com/detail/9n17ns6nm06v?hl=en-US&gl=US>

Rev Hardware Client 2 .ipk (If using REV library)

-   <https://github.com/wpilibsuite/SystemCoreTesting/blob/main/REV.md>

Rev 2027 SPARK MAX / SPARK Flex Firmware

-   <https://github.com/wpilibsuite/SystemCoreTesting/blob/main/REV.md>

## Required Hardware

The following hardware that we have tested with

### Raspberry Pi 5 4 GB

A standard Raspberry Pi 5 with 4GB of memory is as close to the specs as you will get.

-   <https://www.amazon.com/dp/B0FL21867J?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1>

### CAN HAT - NO FD PLUS

This is the exact hat that was used for team 6004 systemcore clone

-   <https://www.amazon.com/Waveshare-2-Channel-Expansion-Compatible-Protections/dp/B0D3GD458Z?s=electronics> - <https://www.waveshare.com/2-ch-can-hat-plus.htm>

### CAN HAT - NO FD

This is the exact hat that was purchased from amazon for this project that does not support FD.

-   <https://www.amazon.com/dp/B087RJ6XGG?ref=ppx_yo2ov_dt_b_fed_asin_title>

### CAN HAT - FD

This is the exact hat that was purchased from amazon for this project that supports CAN FD.

-   <https://www.amazon.com/dp/B07YQTMQTR?ref=ppx_yo2ov_dt_b_fed_asin_title>

### Other CAN HAT

-   [Instructions to use other CAN Hats](./OtherCANHat.md)

## Documentation & Guides

#### SD Card Setup & Cloning

Instructions for preparing a new SD card or cloning an existing SystemCore installation.

-   [Setup & Build Guide](./setup/README.md)
