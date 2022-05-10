# arduino-libflac

FLAC is an Open Source lossless audio codec developed by Josh Coalson from 2001
to 2009. From 2012 to 2021 it was maintained by Erik de Castro Lopo. It continues
to be maintained by various volunteers under the auspices of the Xiph.org Foundation.

## Installation in Arduino

You can git clone this project into the Arduino libraries folder with

```
cd  ~/Documents/Arduino/libraries
git clone https://github.com/pschatzmann/arduino-libflac.git --recursive

```

## Dependencies

This library requires arduino-libopus

## Design

In order to create an Arduino compatible library I executed the following steps:

- Added the project to the original directory
- Symlinked the header and c files into src
- Changed th source code to include flac_config.h when it is compiled by ARDUINO
