This is a mobile sdk for fraud detection that is compatible with the Capacitor cross-platform mobile framework.

### Installation

First you should copy the plugin directory into a place inside your project where it always accessible.

Then you should be installing all the plugin dependencies inside the plugin and building it:

```shell
cd capacitor-collector-plugin
npm install  
npm run build
```

Then, the installation of the plugin is as simple as just running.
```shell
npm install ../capacitor-collector-plugin
npx cap sync
```

### Limitations

Note that Capacitor has limitations regarding the minimum versions of browsers and webcomponents installed on the device. This can limit the ways to test the application on emulators. [Source](https://ionicframework.com/docs/reference/browser-support?_gl=1*1l8esh*_gcl_au*NTA5MzIwMjk3LjE3Mzk0NTUzOTY.*_ga*MTgzMTEwMTE1LjE3Mzk0NTUzOTY.*_ga_REH9TJF6KF*MTczOTUyMzE4NS4yLjEuMTczOTUyMzM3NS4wLjAuMA..#a-note-on-angular-13-support)


### Example

There is an example application inside the plugin directory called `example`. After installing the dependencies of the plugin and buildilng it, I recommend playing around with the example by doing so:

```shell
cd capacitor-collector-plugin
npm install
npx cap sync
npm run build
```

After that you can open the example app and run on different mobile platforms.

```shell
# Android
npx cap open android # Will open the example project in Android Studio where you can build and run it
```

```shell
# iOS
npx cap open ios # Will open the example project in XCode where you can build and run it
```

### Usage

You can use the SDK comfortably from your JavaScript code.

This is the recommended way of starting/initializing the SDK.

```js
import 'capacitor-collector-plugin'

function yourInitializationFunction() {
    // These values are provided by us
    let baseUrl = "<BASE_URL>"
    let cid = "<CID>"
    
    // It is important to call `start` after the initization is complete
    CapacitorCollectorPlugin.initialize({
        baseUrl: baseUrl,
        cid: cid
    }).then(() => {
        CapacitorCollectorPlugin.start()
    })
}
```

It is important to set update values when the app receives them

```js
/**
 * @param userId - usually the id the user uses to login
 * @param csid - the customer session id that is assigned to the current user session (login)
 */
function updateUserInfo(opts: {userId: string, csid: string}) {
    CapacitorCollectorPlugin.setUserId({userId: opts.userId})
    CapacitorCollectorPlugin.setCsid({csid: opts.csid})
    CapacitorCollectorPlugin.sendContext({context: "UPDATING_USER"})
}
```

