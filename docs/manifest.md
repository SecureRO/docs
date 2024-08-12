```
<uses-permission android:name="android.permission.INTERNET" />
```
The SDK is making network requests

```
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```
The SDK is collecting information about currently connected networks

```
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
```
The SDK is collecting information about current connected networks including wifi information

```
<uses-permission  
    android:name="android.permission.ACCESS_COARSE_LOCATION"  
    tools:node="remove" />  
<uses-permission  
    android:name="android.permission.ACCESS_FINE_LOCATION"  
    tools:node="remove" />
```
The SDK is collecting device location information. It is not forced on the client and will not be merged into the consumer `AndroidManifest.xml` 

```
<uses-permission  
    android:name="android.permission.BLUETOOTH_CONNECT"  
    tools:node="remove" />  
<uses-permission  
    android:name="android.permission.BLUETOOTH"  
    android:maxSdkVersion="30"  
    tools:node="remove" />  
<uses-permission  
    android:name="android.permission.BLUETOOTH_ADMIN"  
    android:maxSdkVersion="30"  
    tools:node="remove" />
```
The SDK collects bluetooth status and devices information. It is not forced on the client and will not be merged into the consumer `AndroidManifest.xml`

```
<uses-permission  
    android:name="android.permission.QUERY_ALL_PACKAGES"  
    tools:ignore="QueryAllPackagesPermission"  
    tools:node="remove" />
```
The SDK collects installed applications looking for malware or anything suspicious that can be used to trick the bank customer to share sensitive information. It is not forced on the client and will not be merged into the consumer `AndroidManifest.xml`

```
<uses-permission android:name="android.permission.READ_PHONE_NUMBERS"  
    tools:node="remove"/>  
<uses-permission android:name="android.permission.READ_SMS"  
    tools:node="remove"/>  
<uses-permission android:name="android.permission.READ_PRIVILEGED_PHONE_STATE"  
    tools:ignore="ProtectedPermissions"  
    tools:node="remove"/>
```
The SDK tries to read carrier and phone information, including signal levels, battery levels, amount of sim cards etc. It is not forced on the client and will not be merged into the consumer `AndroidManifest.xml`

```
<uses-permission android:name="android.permission.HIDE_OVERLAY_WINDOWS"  
    tools:node="remove"/>
```
The SDK allows to control when overlays are allowed to be displayed over the application. This permission is required to be able to control that. It is not forced on the client and will not be merged into consumer `AndroidManifest.xml`
