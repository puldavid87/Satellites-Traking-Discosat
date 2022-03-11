# Satellites-Traking-Discosat
https://discosat.dk/index.php/2022/01/groundstation-workshop/

## Information:

The DISCO project will launch 3 satellites into Low Earth Orbit over the next three years. To communicate with the satellites we need to have ground stations that manage the radio communications links for telemetry and data transfer.

The DISCO project is building both fixed ground stations at the participating universities, as well as mobile ground stations that can be loaned to schools in the program.

In this workshop we cover the basics of ground station operation and building including demos and a chance to get hands on experience with a range of equipment, both mobile and fixed equipment that will be later installed at ITU.

## Workshop: Satellites Traking with Open Source Platforms:

This workshop is oriented to build an Open Source satellite tracking. First, we're going to use Python with [Skyflied library](https://rhodesmill.org/skyfield/) and [Celestrak](http://celestrak.com/) to receive the orbit from many satellites. Second, we will use Arduino, one 180 servo motor, and a 360 servo motor to point them. 

### Python and Arduino Installation:

* You can use Python in your web navigator and gmail account: [Google Colab] https://colab.research.google.com/ or install it in your computer: [Anaconda](https://www.anaconda.com/products/individual).
*  With Arduino at the moment, the best option is installing on the computer (there is a beta online version), [Arduino](https://www.arduino.cc/en/software)

### Python Code: 

You can run the code in the selected environment without issues. 

Install the library:

* Google colab: pip install skyfield
* Computer:  Windows Search -> Anconda pront -> pip install skyfield

Test the library:
``` python
#Library
from skyfield.api import load, wgs84

# Load the JPL ephemeris DE421 (covers 1900-2050).
planets = load('de421.bsp')
earth, mars = planets['earth'], planets['mars']

# What's the position of Mars, viewed from Earth?
astrometric = earth.at(t).observe(mars)
ra, dec, distance = astrometric.radec()
print(ra)
print(dec)
print(distance)

```
Get the satellites information:
``` python
#print satellites
stations_url = 'http://celestrak.com/NORAD/elements/stations.txt'
satellites = load.tle_file(stations_url)
print('Loaded', len(satellites), 'satellites')
#loop satellites
by_name = {sat.name: sat for sat in satellites}
for i in by_name:
    print(i)
```
