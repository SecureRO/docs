This page will explain how you can improve the fraud detection capabilities of the collector SDK.

### Navigation detection

#### SceneDelegate

In the scene delegate of your UIKit application you can submit the scenes that are opened as additional contexts to allow the SDK to know that the events that happen are on a different screen. We recommend having a specific prefixes for those contexts for us to be able to distinct the events as special.

The following code is an example of how you could provide additional info to the collector SDK.
Please use unique identifiers for the scenes which are reported changing their state, `scene.title` is used as an example here

```swift
class SceneDelegate: UIResponder, UIWindowSceneDelegate {


    // ... all your logic

    func sceneDidDisconnect(_ scene: UIScene) {
        // ... code

        Collector.shared.sendContext(context: "disconnect_\(scene.title)")
    }

    func sceneDidBecomeActive(_ scene: UIScene) {
        // ... code

        Collector.shared.sendContext(context: "becomeActive_\(scene.title)")
    }

    func sceneWillResignActive(_ scene: UIScene) {
        // ... code

        Collector.shared.sendContext(context: "willResignActive_\(scene.title)")
    }

    func sceneWillEnterForeground(_ scene: UIScene) {
        // ... code

        Collector.shared.sendContext(context: "willEnterForeground_\(scene.titl)")
    }

    func sceneDidEnterBackground(_ scene: UIScene) {
        // ... code

        Collector.shared.sendContext(context: "enterBackground_\(scene.title)")
    }
}
```

#### SwiftUI TBD
