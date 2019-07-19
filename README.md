<img src="https://raw.githubusercontent.com/nightmode/logitech-g27/master/images/header.png" width="888" alt="">

# Logitech G27 Racing Wheel for Node

Bring your [Logitech G27 Racing Wheel](http://support.logitech.com/en_us/product/g27-racing-wheel) into the wonderful world of [Node](https://nodejs.org/en/).

* Subscribe to wheel, pedal, and shifter events.
* Activate simple force feedback effects.
* Set wheel auto-centering and range.
* Customize shift indicator LEDs.

## Requirements

[Node](https://nodejs.org/en/) version 4.0.0 or greater.

## Install

This library uses [node-hid](https://github.com/node-hid/node-hid) behind the scenes. Depending on your OS and Node version, you may have an effortless install. If not, you may want to consult node-hid's [compiling from source](https://github.com/node-hid/node-hid#compiling-from-source) guide for assistance.

```
npm install logitech-g27
```

[Ubuntu](http://www.ubuntu.com/desktop) users will most likely want to remove the `sudo` requirement of interfacing with the wheel. This can be easily accomplished by creating a file at `/etc/udev/rules.d/99-hidraw-permissions.rules` with the following code. After saving the file, reboot and then you can move on to more fun tasks.

```
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", MODE="0664", GROUP="plugdev"
```

## Example

Let's have some fun and make our wheel LEDs light up when we press the gas pedal.

```js
const g = require('logitech-g27')

g.connect(function(err) {
    g.on('pedals-gas', function(val) {
        g.leds(val)
    })
})
```

Vroom vroom sounds optional but encouraged. ^\_^

## API

* [connect](docs/api.md#connect)
  * [options](docs/api.md#options)
* [events](docs/api.md#events)
  * [event map](docs/api.md#event-map)
  * [on](docs/api.md#on)
  * [once](docs/api.md#once)
* [force](docs/api.md#force)
  * [forceConstant](docs/api.md#forceconstant)
  * [forceFriction](docs/api.md#forcefriction)
  * [forceOff](docs/api.md#forceoff)
* [leds](docs/api.md#leds)
* [disconnect](docs/api.md#disconnect)
* [advanced](docs/api.md#advanced)
  * [emitter](docs/api.md#emitter)
  * [relay](docs/api.md#relay)
  * [relayOS](docs/api.md#relayos)

## Support

Help [support this project](https://www.patreon.com/nightmode) on Patreon. Help me caretake and craft new software, videos, and interactive art. All for as little as $1 a month.

In addition to Patreon, here are some other ways you can help this project.

* [Report any issues](https://github.com/nightmode/logitech-g27/issues) on GitHub.
* Share your G27 wheel creation on social media to inspire others.

## License

MIT © [Kai Nightmode](https://twitter.com/kai_nightmode)