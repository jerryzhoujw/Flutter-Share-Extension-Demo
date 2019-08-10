# simple

A simple Flutter project for Share Extesion Demo.

## Branchs
- `Master` branch: only work on simulator,  run on device will give build error.
- `dev/enable_share_extension_for_device` branch: only work on simulator,  run on device will give build error.

## Build Errors:
- Run `Target: Share Extension` on device

```
ld: '[Project_Path]/ios/DerivedData/Products/Debug-iphoneos/FMDB/libFMDB.a(FMDatabase.o)' 
does not contain bitcode. You must rebuild it with bitcode enabled (Xcode setting 
ENABLE_BITCODE)
```

- Run `Target: The Container App` on device
NOTE: this `[CP] Embed Pods Framworks` is same as `[ProjectCompare]`.
```
* Run custom shell script '[CP] Embed Pods Framworks'....
* Validate [Project_Path]/ios/DerivedData/Products/Debug-iphonos/Runner.app/PlugIns/
  ShareExtension.appe(in target: Runner)
* cd [Project_Path]/ios
* builtin-embeddedBinaryValidationUtility [Project_Path]/ios/DerivedData/Products/
  Debug-iphonos/Runner.app/PlugIns/ShareExtension.appex 
    -siging-cert [someID] 
    -info-plist-path [Project_Path]/ios/DerivedData/Products/Debug-iphonos/Runner.app/Info.plist
* error: Embedded binary is not signed with the same certificate as the parent app. 
  Verify the embedded binary target's code sign settings match the parent app's.
    * Embedded Binary Signing Certificate:    Not Code Signed
    * Parent App Signing Certificate:  iPhone Developer: MyName (XXXXX)
```

## Getting Started

This project is a starting point for a Flutter application.

### How to enable Share Extension

1. make sure bundle id on Container APP:  `com.yourbundle.id`
2. make sure Share Extension bundle id:    `com.yourbundle.id.shareExtension` (bundle id before last `.` must be same as Container App)
3. make sure Both app & Share Extension enable `App Groups` with group id:       `group.com.your.goup.id`
4. ShareExtension /Target/ info.plist,
    - Find `NSExtensionActivationRule`: `String`: `TRUEPREDICATE`.
    - Update `String` to `Dictionary`:
    - If you want Share Url in Browser, add bellow in this Dictionary: `NSExtensionActivationSupportsWebURLWithMaxCount` : `Number`: `1`
5. If you want customise UI for Share Extension UI.
 Change MainInterface.storyboard's `ViewController.swift` to `YourCustomizedClass`(subClass to `UIViewController`)
