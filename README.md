# cartera

ZeroW - Raspbian Stretch Lite of_v0.10.0
// buster and 0.11.0 took for ever compiling

Bluetooth - https://www.raspberrypi.org/forums/viewtopic.php?p=963751#p963751

Hyperpixel 
```
curl https://get.pimoroni.com/hyperpixel | bash
./setup.sh
```

Alright, that github comment sums up the problem pretty well : raspberrypi/linux#2264 (comment)

"The rev 1.2 Pi3B lacks the flow control signals to the Bluetooth modem (we ran out of pins), but the rev 1.3 board drops the BT PCM interface and hooks up the flow control. I think what you are seeing is occasional data loss when the FIFOs overflow, something which is hard to avoid in all circumstances. You may be able to lessen the problem by reducing the baudrate on the modem - try editing /usr/bin/btuart, replacing the 921600 with 460800 and rebooting."

It seems the 3B+ has the same problem described here for the first revisions of the 3B.

Reducing the baudrate as explained did the trick for me :)
