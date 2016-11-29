# Java SSD1306 library
Java library for controlling SSD1306-based OLED display (usually the 0.96" mini OLEDs). 
It's not exactly the fastest thing, but it works quite well.

Based on [Adafruit_Python_SSD1306](https://github.com/adafruit/Adafruit_Python_SSD1306).

__You'll need [Pi4J](http://pi4j.com/) library.__

## Build a JAR file with maven

You need [Maven](https://maven.apache.org/) to use the following procedure. Perform the following in the project root folder. 
 
 1. Create the JAR file with the following command: `mvn clean package`
 1. Start example: `sudo java -classpath .:/opt/pi4j/lib/'*' -jar target/ssd1306-0.0.1-SNAPSHOT.jar`

This will execute class ***Pixels*** which tries to draw a sample image via SPI on the OLED.
In case you want to try the I2C bus version (PixelsI2c), execute the following command:

`sudo java -classpath .:./target/ssd1306-0.0.1-SNAPSHOT.jar:/opt/pi4j/lib/'*' eu.ondryaso.ssd1306.examples.PixelsI2c`

For performance reasons, it is advised to build the JAR on a PC and copy the file afterwards to the Raspberry PI.
In case the commands are executed from the same folder where the JAR is located, the `target/` has to be omitted. 

## Connecting
You just have to connect your display to the Raspberry Pi SPI (or I2C) pins. 
I haven't got the I2C thus I don't know if it'll work. Probably not.
Reset pin is not always present and it's not necessary for function.
You can use [this website](http://pi.gadgetoid.com/pinout) for reference.

SPI connection:

| Board pin name | Physical RPi pin | RPi pin name | WiringPi pin |
|----------------|------------------|--------------|--------------|
| DC             | 16               | GPIO23       | 4            |
| CS             | 24               | GPIO8, CE0   | 10           |
| MOSI/Data      | 19               | GPIO10, MOSI | 12           |
| RST            | 22               | GPIO22       | 3            |
| CLK            | 23               | GPIO11, SCKL | 14           |
| GND            | 6, 9, 20, 25     | Ground       |              |
| VCC/3V3        | 1                | 3V3          |              |

I2C connection:

| Board pin name | Physical RPi pin | RPi pin name | WiringPi pin |
|----------------|------------------|--------------|--------------|
| RST            | 22               | GPIO22       | 3            |
| SDA            | 3                | GPIO2, SDA   | 8            |
| SCL            | 5                | GPIO3, SCL   | 9            |
| GND            | 6, 9, 20, 25     | Ground       |              |
| VCC/3V3        | 1                | 3V3          |              |

Remember that Pi4J is using WiringPi numbering. 

## Usage
There are JavaDoc comments in the Display class itself, it should be pretty simple. Also, you can look to the examples.
