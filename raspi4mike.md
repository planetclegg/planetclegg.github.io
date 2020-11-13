

# Ok Mike, so you want to play around with a raspberry pi

(info valid as of November 2020)

## Probably the most confusing thing is all the options:

Right now there are three possible boards that I could recommend:

- Raspberry PI 3B+.  Has 1gb of RAM (a little over a year ago, this was the top of the line model)
- Raspberry PI 4 (current top of the line model, and comes in different RAM capacities 2gb, 4gb, 8gb)
- Raspberry PI 400 (This is a keyboard with raspberry PI 4 hardware inside it.   Super new, will be hard to get for a while)

Ignore the Pi Zero and A+ (which are underpowered and/or made for advanced scenarios), and all the other older models.

The 4 and 400 are considerably faster than the 3B+ and double the RAM capacity or more. the tradeoff is they are a little more expensive and on the 4 you may want to add something to deal with heat (either a fan or a giant heat sink).  They also use a little more power.

For what it's worth, I don't own a 4 yet.  I have several 3's and older running stuff on my network.  But I don't use them as desktops and in fact none are attached to a monitor.  

No matter which of these you get, you need some extra stuff to go with it. You can either acquire all this 
separtely or you can buy a "kit" that might have some of this stuff in it:

## To make a complete raspi client computer you'll need:

- a monitor that has an HDMI input. (You may be able to use a monitor with DVI-D input with a cheap HDMI-to-DVI adapter [looks like this](https://www.amazon.com/Benfei-Bidirectional-Female-Adapter-Gold-Plated/dp/B07CXY79KR/)) 
- HDMI cable.  the 3 uses a full sized HDMI cable, the 4 has MicroDVI ports so it needs a MicroDVI connector on one end.
- A powersupply.  I recommend getting one of the offical ones, but they are generally < $10
- a case (unless you get a 400).  the offical case is great, ~$5. the 3B+ and 4 use different cases.
- a usb keyboard (unless you get a 400).  You can use any old USB keyboard if you happen to have a spare one
- a USB mouse
- a microSD card.  32GB is good to get started. I recommend getting a quality one, like Sandisk.
- if you buy a 4 you may want to buy a fan for it.  This is **not required but**, without active cooling the PI4 it will throttle the CPU under heavy use.  The "Pimoroni Fan Shim" is supposed to be pretty good and cheap fan. *You may need a case thats designed large enough for a fan*

You'll also need a seperate computer and a USB-to-MicroSD adapter (cheap) so you can install Raspbian (the operating system) on the microSD card to get started

## Some suggestions:

Locally, Microcenter sells RaspPI 3b+ and 4 boards at a $10 discount, it's a loss leader for them.   they also sell everything else you could possibly need to get started

Typically the bare 3B+ board goes for $35, but microcenter sells it currently for $25.  It has 1GB of ram.

MSRP pricing on the bare 4 board is ~$35-45 for 2gb, $55 for 4gb, $75 for 8gb (ram).  Microcenter is $10 less for each and has the 2GB board at $25 currently

The 3 and the 4 use slightly different powersupplies (microUSB for 3 vs usb-c for 4)  
Get an offical power adapter.  $7-$15 depending on which one and who you buy it from.

You can buy a kit that has many or all of the accessories (except the monitor), but frequently thats a little
more expensive than buying the parts separately, especially if you already have some of the parts. 


For absolute minimal cost, buy the bare board, power supply and case separately from microcenter.  You can save a couple bucks buying a Sandisk MicroSD from amazon instead of microcenter.  Borrow a USB-to-microusb adapter if need be.

#### I'd say if your use-case is primarily running it for Mathematica and other "desktop" type usages (web browsing, etc), go for a PI4 in 2GB or 4GB, or wait 6 months and get a PI400.  The extra ram is worth a few extra bucks, especially compared to the 3B+.  If you want something that's more for embedded uses (like as a headless server), then the 3B+ might still be a good value.


[microcenter deals](https://www.microcenter.com/search/search_results.aspx?Ntt=raspberry+pi&Ntk=all&sortby=match&N=517&myStore=true)

<https://www.amazon.com/SanDisk-Ultra-microSDXC-Memory-Adapter/dp/B073JYVKNX>


