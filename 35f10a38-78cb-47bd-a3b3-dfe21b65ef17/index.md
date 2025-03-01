# Beginner's guide to Anduril 2

## Summary
Anduril 2 (commonly simply called Anduril now) is a user configurable and powerful firmware for flashlights.  Anduril has a great many features, but you do not need to understand most of what it is capable of to simply use the most common features of the flashlight.

## Factory reset before you begin
Before you begin, it's a good idea to factory reset your light.  This will ensure all configuration settings are back to defaults, and will put the light back in Simple UI or Extended Simple UI.  To do this, turn on the light by clicking the button.  Now unscrew the tailcap a half turn.  Most lights will turn off right away.  If the light goes out, you are ready to proceed.  This also means you are in "tailcap lockout" which means the light cannot be turned on accidentally (nor on purpose), and it will consume absolutely zero power.  
Very few lights, as in, those without anodized threads will remain on with the tailcap unscrewed a half turn.  For those, if the light is still on, keep unscrewing the tailcap until the light goes off.

For clarity, we don't necessarily need to turn the light on to start a factory reset, but turning it on lets us understand how far we need to unscrew the tailcap to cut the power, and we do need the light to be off and the tailcap locked out to start a factory reset.

Now with the light off, hold down the button.  Hold it.  Screw the tailcap all the way back on.  You will see the light get brighter and brighter, while probably flashing a bit.  The brightening is a confirmation delay, in case you do not wish to actually factory reset.  Keep holding the button as we want to continue and do a factory reset.  The light will reach full brightness and then go completely dark.  You can now release the button.

The light is now factory reset and is in Simple UI or Extended Simple UI.

## What is Simple UI?
Simple UI is a mode where most of the configuration menus are disabled, meaning you cannot change nor access most of the light's configuration.  Things like tactical mode, momentary mode (a whole mode where the light can only be turned on momentarily), temperature check, ramp config, channel mode config, sunset timer, and possibly strobe modes will not be available in Simple UI.

Simple UI is a good mode to use if you give the light to someone else, or are new to Anduril.  

Later we'll switch to Advanced UI so we can learn how to change the behavior of the auxiliary LEDs, switch between different LEDs in a multi-channel light, disable different LED combinations in a multi-channel light, etc.

For now, there's a lot we can do with the light in Simple UI, and all of these things we're going to learn carry over verbatim into Advanced UI.  Advanced UI just adds lot of config menus and the other stuff we mentioned a minute ago.

## How to fix the light if it's doing weird things
Before we get started, you should know that no matter what "mode" the light is in, most of Anduril's configuration menus are hidden away behind 6 or 7 consecutive clicks.  Clicking 3 or fewer times is almost always safe, as far as staying out of config menus.  However, if you accidentally click the button 6 or more times and aren't sure what the light is doing, if it won't turn off or turn back on, or is flashing a weird pattern, which will be true if you find yourself in any of the configuration menus, just unscrew the tailcap until the light turns off.  Then screw it back on, and you should be in OFF mode.  If things are still messed up, do a factory reset.

## Lesson 1: Turning on/off the light
To turn the light on/off, simply click the button.  The light will turn on at the last used brightness setting, which we will get into in a moment.

Note that there is a difference between clicking the button, and clicking and holding.  For example, to turn on the light, you would do what Anduril calls a "1C".  Meaning 1 click of the button.  Try 1C.

Shortcuts we know so far:

(From) OFF --> 1C = Turn on with last used brightness level

(From) ON --> 1C = Turn off

## Lesson 2: From off, directly accessing low mode
Turn off the light with 1C.  First, let's show you how to turn on the light in the lowest brightness level, often called moonlight level.  We know that 1C will turn on the light at the last used brightness setting, so now we will learn about 1H, which is to click the button once, and hold it down.  After 1 second, the light will turn on in the lowest brightness mode, and we can release the button.  Try turning off the light with 1C and turning it back on in low with 1H a few times to get a feel for this.  You may want to aim the flashlight at your hand so you can better see the light coming out of it.  Try to avoid pointing it right at your face--if you end up going into a high (brightness) level, you won't be able to see for some time.

Shortcuts we know so far:

OFF --> 1C = Turn on
OFF --> 1H = Low mode

ON --> 1C = Turn off


## Lesson 3: From off, directly accessing the highest brightness mode
For now we are going to gloss over the difference between "ceiling" and "turbo", by simply saying we are going to "turn the light on high".

With the light off, to directly go to high, do a 2C.  This is two clicks.  Don't hold the last one.  The light will come on, briefly darker and then will get very bright.  Turn it off with 1C.  Try this a few times.

We can also go to a "momentary high", such as if we want the highest brightness for only a few seconds, and we want to simply hold down the button as long as we need the light, and upon release the light will auto-turn off.  To access momentary high, do a 2H.  You will see that as soon as you stop holding the button, the light turns off.  We can see this is different than turning the light onto high with 2C.

But now we have two options for accessing high, and one for accessing low.


Shortcuts we know so far:

OFF --> 1C = Turn on with last used brightness level
OFF --> 1H = Low mode
OFF --> 2C = High mode
OFF --> 2H = Momentary high mode

ON --> 1C = Turn off

But what about something in the middle?

## Lesson 4: The brightness ramp
A lot of lights have a few brightness settings, perhaps a low, medium, and high, or maybe 4 different brightness levels, etc.  Anduril has an infinite amount of brightness levels, and you can gradually go from any brightness setting all the way up to high, or all the way down to low, stopping at just the right light level for your task.

By default, the brightness ramp is a smooth ramp, which is officially referred to as "smooth ramp".  The other setting is "stepped ramp", where the light jumps through perhaps 6 different light levels as you go from low to high or vice versa.  

Let's do 1C to turn the light on at the last used brightness level.  We should note that this means Anduril has brightness memory--it can remember what brightness level you last used (and channel, but we'll get into that later).  Now that the light is on, let's hold down the button.  The light will begin gradually getting brighter, and eventually it will blink, indicating max brightness.  Now, let go of the button and immediately (within 1 second), hold it down again.  The light will begin going the other way--getting darker until you reach moonlight levels.

Try this a few times, holding down the button to see the light get brighter, then release at some point and within 1 second hold down the button again to go the other way.  

Anduril has options for how it's brightness memory works, as well as how fast the light ramps up/down, and whether it is stepped or smooth, if it's stepped then how many steps, but we don't need to understand how to modify these things right now.

Shortcuts we know so far:

OFF --> 1C = Turn on with last used brightness level
OFF --> 1H = Low mode
OFF --> 2C = High mode
OFF --> 2H = Momentary high mode

ON --> 1C = Turn off


## Lesson 5: Checking the battery level
Anduril has the built-in ability to tell us the voltage of the battery.  A fully charged battery will have about 4.2 volts.  A half full one is about 3.6 volts, and at 2.5 to 3.0 volts the battery is completely dead, the user should stop discharging the battery and the battery should be charged.  Anduril includes low voltage protection, so if your battery is drained to about 2.9 volts, Anduril will stop discharging the battery and turn off and stay off.  Though it depends on which exact lithium ion cell you are using, generally the cell needs to always be above 2.5 to 3.0 volts to maintain it's internal integrity.  Lithium ion batteries with a nominal voltage of 3.6 volts that get discharged below 2.5 volts will suffer, and may lose enough internal integrity to become unsafe.

To check the battery level, from off, 3C.  As soon as you let go of the button on the third click, the light will begin flashing.  Count the flashes.  4 flashes, a pause, then 2 flashes would be 4.2 volts.  4 flashes followed by a super fast flash would be 4.0 volts.  Super fast flashes are a 0.  Some lights will give more than 2 digits.  

So for example, a flash pattern with all long flashes like long long long pause long long would be 4.2 volts.  
Some lights will give one extra digit, such as 4.05 volts.  This would look like long long long long short long long long long long.

The first time you do 3C, just try to get a feel for the flashing pattern. When in Simple UI, after the light is done flashing the battery voltage, it will turn back off.  One way to tell if you are in Simple or Advanced UI is from off to do 3C.  If the battery voltage is displayed once, you are in Simple UI.  If there is a longer pause and the battery voltage is repeated, then a longer pause and voltage is repeated again, endlessly, you are in Advanced UI.   In Advanced UI the battery voltage is repeated endlessly and you have to press 1C to turn the light off.

Try 3C a few times until you feel confident about reading your batteries voltage.  You can try this over the course of the first day with your light to watch the slow decrease in voltage.  It's helpful to know the voltage of the cell, so that you know when to charge, and how much energy you have left.

## Lesson 6: Post off voltage display
This presumes your light has either auxiliary LEDs, or an RBG backlight under the button.  To tell, turn the light on, then off.  If immediately after turning off your light, for about 4 seconds you see a color (most likely it will be blue or green) coming from underneath your button or from tiny LEDs at the front of the light, then you have one or both of these.

Auxiliary LEDs, which are always RGB, are tiny LEDs that usually surround the main LED emitter, and are very dim additional LEDs used by Anduril.  Both aux LEDs and RBG button backlights can be used to ALSO keep you informed about your battery voltage, using a color-based system, basically ROYGBIV but backwards.  So fully charged, 4.2 volts will be indicated with a purple color (blue+red).   You might also see blue if you are somewhat below a full charge.  Then as your battery level drops, you will see blue, then cyan, then green, then yellow, then red, then black (as in nothing).

Presuming your battery is fully charged, your light may have an RGB button, indicated by a blue light coming from underneath your button.  The light will be green if you are half charged (all batteries come half charged at 3.6 volts).

If neither of these happen, as in, after turning on the light with 1C and then off with 1C, if you see absolutely no colored light coming from the button or the front of the light, then you can still rely on the 3C from off battery voltage flash-out pattern to see battery voltage.

Some lights, in addition to the (RGB) post off voltage display and the off-->3C battery voltage flash pattern will also keep the RBG button backlight on while the light is ON.  In this case you can see the battery voltage via colors even when the light is on, in realtime.

## Lockout mode:
TODO

## Multi-channel lights
TODO

## Switching to Advanced UI
TODO

## Link to Anduril manual?

## Transition to Anduril diagram/manual

*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


