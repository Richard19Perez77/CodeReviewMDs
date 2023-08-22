# AndroidCodeSnippets
Android API Code and Configuration

`Intent` API 12 - Deep Links "Door Dash" 

https://doordash.engineering/2022/01/25/your-deep-links-might-be-broken-web-intents-and-android-12/

```
Starting in Android 12 (API level 31), a generic web intent resolves to an activity in your app only if your app is approved for the specific domain contained in that web intent. If your app isn't approved for the domain, the web intent resolves to the user's default browser app instead.
```
```
val webpage: Uri = Uri.parse("https://www.doordash.com/store/fusian-columbus-76690/")
val intent = Intent(Intent.ACTION_VIEW, webpage)
startActivity(intent)
```
```
<activity
    android:name="com.doordash.DeepLinkActivity"
    android:theme="@style/Theme.Consumer.DoorDash">
        <intent-filter>
            <action android:name="android.intent.action.VIEW" />

            <category android:name="android.intent.category.BROWSABLE" />
            <category android:name="android.intent.category.DEFAULT" />

            <data
                android:host="www.doordash.com"
                android:pathPrefix="/store"
                android:scheme="https" />

        </intent-filter>
</activity>
```
```
<activity
    android:name="com.doordash.DeepLinkActivity"
    android:theme="@style/Theme.Consumer.DoorDash">
        <intent-filter android:autoVerify="true" tools:targetApi="m">
        </intent-filter>
</activity>
```
```
Optionally add tools:targetApi=”m” to appease the Lint warning
```
`assetlinks.json`
```
[{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "<Your App’s package name>",
    "sha256_cert_fingerprints":
    ["<Your App’s SHA256 finger print>"]
  }
}]
```
Or with 3x domains
```
 [{
    "relation": ["delegate_permission/common.handle_all_urls"],
    "target": {
      "namespace": "android_app",
      "package_name": "com.dd.doordash",
      "sha256_cert_fingerprints": ["93:6F:83:B9:14:21:6D:8A:87:A7:97:EF:FB:5C:A9:D4:50:0B:D2:78:D8:92:07:9F:DB:0D:5D:05:FE:F2:10:B5"]
    }
  },
  {
    "relation": ["delegate_permission/common.handle_all_urls"],
    "target": {
      "namespace": "android_app",
      "package_name": "com.trycaviar.customer",
      "sha256_cert_fingerprints": ["2A:59:23:CF:17:46:ED:DC:12:31:3A:99:6A:A3:8D:11:A7:56:7B:08:7E:74:A6:F0:B3:A5:60:81:63:FA:7B:D0"]
    }
  }
]
```
To find the SHA256 fingerprint, use Java’s keytool command. If the keystore is available, use the following: 
`keytool -list -v -keystore [my-release-key.keystore]. Or if working with the .apk file, use this: keytool -printcert -jarfile [path-to-apk]`

After generating the digital asset links file, deploy it to the host (or hosts if handling multiple domains) under a .well_known directory such as https://www.doordash.com/.well-known/assetlinks.json

Verify changes on Android
```
adb shell am start -a android.intent.action.VIEW \
    -c android.intent.category.BROWSABLE \
    -d "https://www.doordash.com/store/fusian-columbus-76690/"
```

Summary
To summarize, here are the key takeaways from this post: 

1. Utilize android:autoVerify=”true” in the Android Manifest within intent filters that respond to intents with http links.
2. Generate an assetlinks.json digital asset file to create a link between the host and the application. 
3. Work with your infrastructure team to deploy the assetlinks.json file to the host(s) or hosts (if you are handling multiple domains).


