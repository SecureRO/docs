This is a mobile sdk for fraud detection that is compatible with the Capacitor cross-platform mobile framework.

### Installation

First you should copy the plugin directory into a place inside your project where it always accessible.

Then, the installation of the plugin is as simple as just running.
```shell
npm install ../capacitor-collector-plugin
npx cap sync
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

