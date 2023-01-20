---
layout: post
title: Look at Xbox 360 Slim RF board
---

The RF board is used in Xbox for connecting wireless controllers, front panel buttons, and front panel led control. Currently research about this is very limited, so I decided to have a little bit of fun.

### How does an RF Board look?

There is two main models for the slim console, altho there seems to also be some pcb revisions to these. The main difference is that Model 1410 is using two chips while Model 1409 uses one.

#### Model 1409
![X360 RF Model 1409 Front](/assets/images/x360-rf-model-1409-front.png)
![X360 RF Model 1409 Back](/assets/images/x360-rf-model-1409-back.png)

#### Model 1410
![X360 RF Model 1410 Front](/assets/images/x360-rf-model-1410-front.png)
![X360 RF Model 1410 Back](/assets/images/x360-rf-model-1410-back.png)

Both of these are interchangable so you can swap between them without a problem or any modifications needed, therefore they use the same connector. With a bit of research this connector pinnout has been publicly documented and is as follows:
![X360 RF Slim Pinout](/assets/images/x360-rf-slim-pinout-pcb.png)

You might have noticed that this picture looks suspiciously like a PCB render... well you are correct as I created this pinout with KiCad to dust off my pcb design skills. The pcb was ordered via [OshPark](https://oshpark.com/) After Dark service and the final result looks like this:

![X360 RF Slim Pinout Keychain](/assets/images/x360-rf-slim-pinout-keychain.png)

Based on the pinout there is two interesting buses:
#### USB
This is used for controller data and you can see that people have created resources to connect it to normal pc and use it as a Xbox 360 Wireless PC adapter. One of these projects is linked here: [Connecting a salvaged Xbox 360 RF module to a desktop computer](http://www.appliedcarbon.org/xboxrf.html)

#### SMC data bus
This bus is connected to the SMC inside xbox to send various commands like initialize rf, turn on led, etc.
Initial research shows that is is similar to I2C but its more likely this is actually a derivative called SMBus. Trying to play around with this databus I captured some data with logic analyzer:
![X360 RF Databus Logic Analyzer](/assets/images/x360-rf-databus-logicanalyzer.png)

While looking avaliable commands from the previously linked project unfortunately those commands work only for the Older RF modules for Phat revisions of the 360, but I used the same command size and bruteforced some behaviour:
<video controls>
  <source src="/assets/videos/x360-rf-slim-led-test.webm" type="video/webm">
</video>

That is it for now... I have been experimenting with other parts and will do more posts in the future.
