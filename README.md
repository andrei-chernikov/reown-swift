## About this fork

This is an unofficial fork of [Reown Swift](https://github.com/reown-com/reown-swift), maintained to improve macOS compatibility and provide additional customization options.

### Changes

**macOS compatibility — [upstream PR #342](https://github.com/reown-com/reown-swift/pull/342)**

- Fixes macOS compilation errors in `WalletConnectSign`.
- Adds the missing `Foundation` import.
- Guards iOS-only `UIApplication` calls.
- Allows unsupported Link Mode operations to fail explicitly so callers can fall back to Relay transport.

**AppKit customization**

- Exposes `ChainPresets.ethChains` publicly, allowing applications to customize the available blockchain networks.

### Compatibility and limitations

The macOS fix has been tested with the `WalletConnect` Swift package. Native macOS support for the complete ReownAppKit UI is not guaranteed.

This fork is experimental and is not officially maintained or endorsed by Reown.

**Upstream status:** The macOS fix has been submitted as PR #342 but has not yet been merged.

**Patch branch:** `fix/macos-missing-foundation-import`

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
