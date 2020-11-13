# More Raspi stuffs:

## We talked about Mathematica

It comes with a raspi OS called "Raspian".  really good OS to start with

[raspi mathematica tutorial](https://projects.raspberrypi.org/en/projects/getting-started-with-mathematica)


## Pi "HAT"s are plug-in boards for RASPIs

you can peruse some examples of these on [adafruit](https://www.adafruit.com/category/405) or the 
[pinout](https://pinout.xyz/boards) site.  There are literally hundreds of different HATs boards out there.

*Of note, if you run a PI 4 with a fan, from what I understand it can be  a little tricky to use a HAT board as well (but it can be done)*

## We talked about temp sensors.

This is a little geeky so I'll try to lay out a general approach.  You'll need:

- Some commodity off the shelf wireless temperature sensor(s). I recommend Acurite or Ambient weather.  (certain ones)
- an RTL-SDR.  This is a software defined radio that can receive the transmissions (and oh.. man... do these things have all sorts of uses)
- some software to pull it all together  (rtl-sdr & rtl_433 to decode the signals, and some more stuff to do useful stuff with data you get).


### Wireless temp sensors.

Either go all Acurite or all Ambient weather.  Right now Acurite looks a little better for most use cases:

- Ambient weather <https://www.amazon.com/Ambient-Weather-F007TH-Wireless-Thermo-Hygrometer/dp/B00C3HBRIW/>
- Acurite 1 <https://www.amazon.com/dp/B01G7BE9WK>
- Acurite 2 <https://www.amazon.com/dp/B00T0K8NXC/>

### the SDR:

Just get this one.  Best bang for the buck   <https://www.amazon.com/RTL-SDR-Blog-RTL2832U-Software-Defined/dp/B011HVUEME/>


### the software.

This part is a bit more complicated, and you probably want Joel or I to help with this  bit, depending on your needs.  Ive done some really rough work for a server that can track 7 days of data already, and you can see what I've done here (you can see a screenshot if you scroll down):

<https://github.com/planetclegg/temperature-server>






