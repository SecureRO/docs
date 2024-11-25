## General usage as `.aar` file

### Including the dependency

Include the following dependencies in your application `build.gradle` file

```groovy
dependencies {
// ... your dependencies

// Collector dependencies
implementation 'com.google.code.gson:gson:2.10.1'  
implementation 'com.google.android.gms:play-services-location:21.0.1'  
implementation 'org.jetbrains.kotlinx:kotlinx-coroutines-android:1.6.4'  
implementation 'com.squareup.okhttp3:okhttp:4.11.0'  
implementation 'com.squareup.moshi:moshi-kotlin:1.14.0'  
implementation 'com.google.android.gms:play-services-safetynet:18.0.1'  
implementation 'com.google.guava:guava:31.0.1-jre'  

// Optional Huawei location dependency
implementation 'com.huawei.hms:location:6.12.0.300'  

// Optional Play Integrity dependency
implementation 'com.google.android.play:integrity:1.4.0'

// Optional dnsjava dependency in cases we see dns lookup issues
implementation 'dnsjava:dnsjava:3.6.1'

// Collector dependency
implementation files('libs/collector-release.aar')
}
```

The collector uses, but doesn't require the following permissions in the `AndroidManifest.xml`. Please make sure to include the ones you think are appropriate for your application [Collector manifest permissions and usage](/manifest)

### Usage in code

 
```kotlin
class MyApp: Application() {
	private val BASE_URL = "base url provided by us"
	private val CID = "customer id provided by us"
	
	fun onCreate() {
		// It is preferred that the collector SDK is initialized from the Application class, but it can be initialized from any place before the SDK is used
		val collector = CollectorAgent.initialize(this, BASE_URL, CID)

		// mainly used to print the logs into logcat for debugging
		collector.isDebug = false
	}
}
```

```kotlin
val collector = CollectorAgent.get()

// call when the user session id is updated or available
collector.setCSID(CSID)

// call when the user id is updated or available
collector.setUserID(UserID)

// call when the state of the application is changed. Different contexts can trigger different state updates inside the SDK
collector.sendContext("CONTEXT")
```

#### Logging failed user logins 

There is a way to report failed user logins, the backend could match the amount of failed login attempts with the userids that are being used to authenticate to correct the possibility of fraud happening from the specific device.

```kotlin
val collector = CollectorAgent.get()

// failed login using password
collector.sendFailedLogin(uid = userId, method = "password")

// failed login using otp
collector.sendFailedLogin(uid = userId, method = "otp")

// failed login using biometric
collector.sendFailedLogin(uid = userId, method = "biometric")
```

