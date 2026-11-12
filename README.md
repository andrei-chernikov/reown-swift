## About this fork

This is an unofficial fork of [Reown Swift](https://github.com/reown-com/reown-swift), maintained for macOS compatibility and additional AppKit customization.

### Branches

| Branch | Contents |
| --- | --- |
| [`develop`](https://github.com/andrei-chernikov/reown-swift/tree/develop) | Upstream `develop` code plus these fork notes. The compatibility patches are on the branches below. |
| [`fix/macos-missing-foundation-import`](https://github.com/andrei-chernikov/reown-swift/tree/fix/macos-missing-foundation-import) | Only the `LinkEnvelopesDispatcher.swift` macOS fix, rebased onto upstream `develop`. Submitted as [PR #342](https://github.com/reown-com/reown-swift/pull/342). |
| [`macos-2.4.0`](https://github.com/andrei-chernikov/reown-swift/tree/macos-2.4.0) | Upstream 2.4.0 plus the macOS fix and public `ChainPresets.ethChains` customization. |

### Install the patched fork

To use both fixes, select `macos-2.4.0` in Xcode or pin its current revision in `Package.swift`:

```swift
.package(
    url: "https://github.com/andrei-chernikov/reown-swift.git",
    revision: "24047d270759e2189f994e348d2c563778865bba"
)
```

### Compatibility and upstream status

The macOS patch adds the missing `Foundation` import and guards iOS-only `UIApplication` calls in `WalletConnectSign`. Unsupported Link Mode operations return an explicit error; the patch does not add automatic fallback to Relay.

The scope is the `WalletConnect` package product. Native macOS support for the complete ReownAppKit UI is not guaranteed. The separate `ChainPresets` change lets apps customize the available networks.

[PR #342](https://github.com/reown-com/reown-swift/pull/342) is awaiting upstream review. The duplicate [PR #367](https://github.com/reown-com/reown-swift/pull/367) is closed; `macos-2.4.0` remains available for existing consumers.

This fork is experimental and is not officially maintained or endorsed by Reown.

---

## Upstream project documentation

The installation URLs below refer to the official upstream package. Use the fork installation above for the patched version.

# Reown WalletKit & AppKit - Swift

![CI main](https://github.com/reown-com/reown-swift/actions/workflows/ci.yml/badge.svg?branch=main)
![CI develop](https://github.com/reown-com/reown-swift/actions/workflows/ci.yml/badge.svg?branch=develop)

Swift implementation of WalletKit and AppKit for native iOS applications.
## Requirements
- iOS 13
- XCode 13
- Swift 5

## Documentation & Usage
- In order to build API documentation in XCode go to Product -> Build Documentation
- [Getting started with wallet integration](https://docs.walletconnect.com/2.0/swift/sign/installation)
- [Beginner guide to WalletConnect v2.0 for iOS Developers](https://medium.com/walletconnect/beginner-guide-to-walletconnect-v2-0-for-swift-developers-4534b0975218)
- [Protocol Documentation](https://github.com/WalletConnect/walletconnect-specs)
- [Glossary](https://docs.walletconnect.com/2.0/introduction/glossary)
- [Migration guide to AppKit](https://gist.github.com/llbartekll/a6fb18b48af837bcc46bb75b3eeaa781)
- [Migration guide to WalletKit](https://gist.github.com/llbartekll/a6fb18b48af837bcc46bb75b3eeaa781)


## Installation
### Swift Package Manager
Add .package(url:_:) to your Package.swift:
```Swift
dependencies: [
    .package(url: "https://github.com/reown-com/reown-swift", .branch("main")),
],
```
### Cocoapods
Add pod to your Podfile:

```Ruby
pod 'reown-swift'
```
If you encounter any problems during package installation, you can specify the exact path to the repository
```Ruby
pod 'reown-swift', :git => 'https://github.com/reown-com/reown-swift.git', :tag => '1.0.0'
```
## Setting Project ID
Follow instructions from *Configuration.xcconfig* and configure PROJECT_ID with your ID from WalletConnect Dashboard
```
// Uncomment next line and paste your project id. Get this on: https://cloud.walletconnect.com/sign-in
// PROJECT_ID = YOUR_PROJECT_ID
// To use Push Notifications on the Simulator you need to grab the simulator identifier
// from Window->Devices and Simulators->Simulator you're using->Identifier
SIMULATOR_IDENTIFIER = YOUR_SIMULATOR_IDENTIFIER
```
## Example Apps
open `Example/ExampleApp.xcodeproj`


## Guides

- [Artifacts sometimes not available in Actions -> Build name -> Artifacts?](./docs/guides/downloading_artifacts.md)
