# URLEmbeddedView

[![Platform](http://img.shields.io/badge/platform-ios-blue.svg?style=flat)](https://developer.apple.com/iphone/index.action)
[![Language](http://img.shields.io/badge/language-swift-brightgreen.svg?style=flat)](https://developer.apple.com/swift)
[![Version](https://img.shields.io/cocoapods/v/URLEmbeddedView.svg?style=flat)](http://cocoapods.org/pods/URLEmbeddedView)
[![License](https://img.shields.io/cocoapods/l/URLEmbeddedView.svg?style=flat)](http://cocoapods.org/pods/URLEmbeddedView)

![](./SampleImages/sample2.gif) ![](./SampleImages/sample.gif)


## Features

- [x] Simple interface for fetching Open Graph Data
- [x] Be able to display Open Graph Data
- [x] Automatically caching Open Graph Data
- [x] Automatically caching Open Graph Image
- [x] Tap handleable
- [x] Clearable image cache
- [x] Clearable data cache
- [ ] Configurable expire date for cache

## Usage

To run the example project, clone the repo, and run `pod install` from the Example directory first.

```swift
let embeddedView = URLEmbeddedView()
embeddedView.loadURL(urlString)
```

## Layouts

- Default

<img src="SampleImages/sample01.png" width="320">

- No Image

<img src="SampleImages/sample03.png" width="320">

- No response

<img src="SampleImages/sample02.png" width="320">

## Customization

```swift
embeddedView.textProvider[.Title].font = .boldSystemFontOfSize(18)
embeddedView.textProvider[.Title].fontColor = .lightGrayColor()
embeddedView.textProvider[.Title].numberOfLines = 2
//You can use ".Title", ".Description", ".Domain" and ".NoDataTitle"
```

## Data and Image Cache

You can get Open Graph Data with `OGDataProvider`.

```swift
OGDataProvider.sharedInstance.fetchOGData(urlString: String, completion: ((OGData, NSError?) -> Void)? = nil) -> NSURLSessionDataTask?
OGDataProvider.sharedInstance.deleteOGData(urlString: String, completion: ((NSError?) -> Void)? = nil)
OGDataProvider.sharedInstance.deleteOGData(ogData: OGData, completion: ((NSError?) -> Void)? = nil)
```

You can get UIImage with `OGImageProvider`.

```swift
OGImageProvider.sharedInstance.loadImage(urlString: String, completion: ((UIImage?, NSError?) -> Void)? = nil) -> NSURLSessionDataTask?
OGImageProvider.sharedInstance.clearMemoryCache()
OGImageProvider.sharedInstance.clearAllCache()
```

## OGData Properties

```swift
@NSManaged public var createDate: NSDate
@NSManaged public var imageUrl: String
@NSManaged public var pageDescription: String
@NSManaged public var pageTitle: String
@NSManaged public var pageType: String
@NSManaged public var siteName: String
@NSManaged public var sourceUrl: String
@NSManaged public var updateDate: NSDate
@NSManaged public var url: String
```

## Installation

URLEmbeddedView is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "URLEmbeddedView"
```

## Use in Objective-C

```objective-c
#import <URLEmbeddedView/URLEmbeddedView-Swift.h>

- (void)viewDidLoad {
    [super viewDidLoad];
    URLEmbeddedView *embeddedView = [[URLEmbeddedView alloc] init];
    [self.view addSubView:embeddedView];
    [embeddedView loadURL:@"https://github.com/" completion:nil];
}
```

[Here](./URLEmbeddedViewSample/URLEmbeddedViewSample/OGObjcSampleViewController.m) is Objective-C sample.

## Special Thanks

- [Kanna(鉋)](https://github.com/tid-kijyun/Kanna) is a great XML/HTML parser for Mac OS X and iOS. (Created by [@tid-kijyun](https://github.com/tid-kijyun))
- [CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift) is a greate Crypto related functions and helpers for Swift. (Created by [@krzyzanowskim](https://github.com/krzyzanowskim))

## Requirements

- Xcode 7.0 or greater
- iOS 8.0 or greater
- [MisterFusion](https://github.com/szk-atmosphere/MisterFusion) - Swift DSL for AutoLayout
- [Kanna(鉋)](https://github.com/tid-kijyun/Kanna)
- [CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift)
- UIKit
- CoreData
- CoreGraphics

## Author

Taiki Suzuki, s1180183@gmail.com

## License

URLEmbeddedView is available under the MIT license. See the LICENSE file for more info.
