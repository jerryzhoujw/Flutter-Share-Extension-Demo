# simple

A simple Flutter project for Share Extesion Demo.

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
