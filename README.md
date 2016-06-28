# Reading Arduinos DHT22 sensor from USB

This simple shell script reads data from the Arduino’s DHT22 sensor via USB and 
sends it to a [Carbon/Graphite](https://pypi.python.org/pypi/carbon/) server.
Therefore it reads the system's USB interface (for me it was /dev/ttyUSB0)
and sends it to a Carbon server. Each line read from USB has added a 
PREFIX string and the current time stamp.

To get data in the right format, the example from [DHTlib](https://github.com/adafruit/DHT-sensor-library)
needs to be slightly adapted. You can set temperature also to Fahrenheit instead of Celcius (see DHTLib example for how).
Once the sketch is uploaded to the Arduino, data will be received in the right format.

Using the included systemd service file allows to start the script at startup time.
A log file is kept in /var/log/dht22.log

## Install
* Copy service file to /etc/systemd/system/dht22-readings.service
* Copy bash file to  /usr/local/bin/dht22-readings
* Use Arduino IDE to compile and upload sketch (needs [DHTlib](https://github.com/adafruit/DHT-sensor-library) to be available)
