# react-native-zeroconf

> Basic Zeroconf implementation for React-native

Get running services advertizing themselves using Zeroconf implementations like Avahi, Bonjour or NSD.

### Install

    npm i -S react-native-zeroconf

 - Right click on the `Libraries` folder in XCode, and add `RNZeroconf.xcodeproj`
 - Go to your *Build Phases*, under *Link Binary with Libraries*, add `libRNZeroconf.a`
 - Click on the `RNZeroconf.xcodeproj` in the `Libraries` folder, search *Header Search Paths* and add `$(SRCROOT)/../../react-native/React` if it's not.

### API

    import Zeroconf from 'react-native-zeroconf';
    const zeroconf = new Zeroconf();

##### Methods

###### `scan(type = 'http', protocol = 'tcp', domain = 'local.')` Start the zeroconf scan

This will initialize the scan from the `Zeroconf` instance. Will stop another scan if any is running.

###### `stop()` Stop the scan

If any scan is running, stop it. Otherwise do nothing.

###### `getServices()` Returns resolved services

Will return all names of services that have been resolved.

##### Events

    zeroconf.on('start', () => { console.log('The scan has started.'); });

###### `start` Triggered on scan start
###### `stop` Triggered on scan stop
###### `found` Triggered when a service is found

Broadcast a service info object containing the service name as soon as it is found.

###### `resolved` Triggered when a service is resolved

Broadcast a service info object containing the service name, addresses, port, full name, and hostname.

Example:

    {
      "host":"XeroxPrinter.local.",
      "addresses":[ // can be either IPv4 or IPv6
        "192.168.1.23",
        "fe80::aebc:123:ffff:abcd"
      ],
      "name":"Xerox Printer",
      "fullName":"XeroxPrinter.local._http._tcp.",
      "port":8080
    }

###### `remove` Triggered when a service is removed

Broadcast a service info object containing the service name.

###### `update` Triggered either when a service is found or removed
###### `error` Triggered when an error occurs

### Webpack

This component uses ES6. If using webpack you should launch `babel` on the `Zeroconf.js` file.
