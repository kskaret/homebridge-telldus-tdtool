[![Build Status](https://travis-ci.org/amlinger/homebridge-telldus-tdtool.svg?branch=master)](TravisBuild)

# Homebridge Telldus tdtool

A [Homebridge](Homebridge) plugin for TellStick without Telldus Live,
interfaced with the CLI tool [`tdtool`](tdtool). This will therefore
require `tdtool` to be present, and runnable, on your server running
Homebridge.

`tdtool` can be found as a part of `telldus-core`, provided by Telldus.

Since it relies on `telldus-core`, only TellStick Duo and TellStick are
supported. TellStick net will support `telldus-core`,
[eventually](TellStickCompability).

## Installation

Install this plugin globally by typing the following.
```bash
npm install -g homebridge-telldus-tdtool
```
Installing the package globally is not a requirement, but makes it easier if
you have also installed Homebridge globally. Otherwise, just install this
package in the directory which you have set up Homebridge to watch for
plugins in.

You must then include
```json
{
  "platform" : "Telldus-TD-Tool",
  "name" : "Telldus-TD-Tool"
}
```
in your list of platforms, in the configuration file of Homebridge. This by
default resides in `~/.homebridge/config.json` and should look something
like the following when you have added this platform:
```json
{
  "bridge": {
    "name": "Homebridge",
    "username": "CC:22:3D:E3:CE:30",
    "port": 51826,
    "pin": "031-45-154"
  },
  "platforms": [{
    "platform" : "Telldus-TD-Tool",
    "name" : "Telldus-TD-Tool"
  }]
}
```

### Building it yourself

This module is written in ES6. To support earlier versions of Node, this is
transpiled using Babel to regular ES5. To build it yourself, make sure you have
installed all the development dependencies (this is usually done by default
with `npm install`). To make sure, you can run:
```sh
npm install --only=dev
```
after you have issued the regular install command.

To build the dist folder, then run
```bash
npm run build
```

## Dependencies & Trade-offs
This plugin depends on `tellstick.conf-parser`. This is because `tdtool` does
not output the model of a connected device, making it not possible to provide
a devices characteristics for Homebridge unless we peek in TellSticks
configuration file and check the model there.

## Contribute
1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request!

<!---
The links below are used for referencing above.
-->
[TravisBuild]: https://travis-ci.org/amlinger/homebridge-telldus-tdtool
[tdtool]: http://developer.telldus.se/doxygen/
[Homebridge]: https://github.com/nfarina/homebridge
[TellStickCompability]: http://developer.telldus.se/
