# SwiftProgressHUD

[![Build Status](https://travis-ci.org/matej/MBProgressHUD.svg?branch=master)](https://travis-ci.org/matej/MBProgressHUD) [![codecov.io](https://codecov.io/github/matej/MBProgressHUD/coverage.svg?branch=master)](https://codecov.io/github/matej/MBProgressHUD?branch=master)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage#adding-frameworks-to-an-application) [![CocoaPods compatible](https://img.shields.io/cocoapods/v/MBProgressHUD.svg?style=flat)](https://cocoapods.org/pods/MBProgressHUD) [![License: MIT](https://img.shields.io/cocoapods/l/MBProgressHUD.svg?style=flat)](http://opensource.org/licenses/MIT)

`MBProgressHUD` is an iOS drop-in class that displays a translucent HUD with an indicator and/or labels while work is being done in a background thread. The HUD is meant as a replacement for the undocumented, private `UIKit` `UIProgressHUD` with some additional features.

[![](https://cloud.githubusercontent.com/assets/91322/26737574/95128ef6-477f-11e7-8b3a-456b2b585e75.png)](https://cloud.githubusercontent.com/assets/91322/26737572/94a137a6-477f-11e7-9778-6266006f2dba.png)
[![](https://cloud.githubusercontent.com/assets/91322/26737576/951cc0c4-477f-11e7-9bc4-891cbbe70f80.png)](https://cloud.githubusercontent.com/assets/91322/26737575/95178c6c-477f-11e7-8df9-03aeeca5d39d.png)
[![](https://cloud.githubusercontent.com/assets/91322/26737577/9523169a-477f-11e7-83d9-c1a55b724c0a.png)](https://cloud.githubusercontent.com/assets/91322/26737578/95235920-477f-11e7-9968-9ecf506aba06.png)
[![](https://cloud.githubusercontent.com/assets/91322/26737579/954371ce-477f-11e7-85f8-660807a7f35e.png)](https://cloud.githubusercontent.com/assets/91322/26737573/95048432-477f-11e7-8f1d-4d5736b10488.)
[![](https://cloud.githubusercontent.com/assets/91322/26737581/954e3c9e-477f-11e7-93d9-2a8e2e0e7dd0.png)](https://cloud.githubusercontent.com/assets/91322/26737580/954aff70-477f-11e7-9634-5802daea2dee.png)
[![](https://cloud.githubusercontent.com/assets/91322/26737583/955ba17c-477f-11e7-93aa-d952fb0bbce3.png)](https://cloud.githubusercontent.com/assets/91322/26737582/9552886c-477f-11e7-8e90-46acd9a8527c.png)
[![](https://cloud.githubusercontent.com/assets/91322/26737585/95a31822-477f-11e7-9ca6-b33ceb3a3f49.png)](https://cloud.githubusercontent.com/assets/91322/26737584/956392f6-477f-11e7-918f-717a42758156.png)

**NOTE:** The class has recently undegone a major rewrite. The old version is available in the [legacy](https://github.com/jdg/MBProgressHUD/tree/legacy) branch, should you need it. 

## Requirements

`MBProgressHUD` works on iOS 6+ and requires ARC to build. It depends on the following Apple frameworks, which should already be included with most Xcode templates:

* Foundation.framework
* UIKit.framework
* CoreGraphics.framework

You will need the latest developer tools in order to build `MBProgressHUD`. Old Xcode versions might work, but compatibility will not be explicitly maintained.

## Adding MBProgressHUD to your project

### CocoaPods

[CocoaPods](http://cocoapods.org) is the recommended way to add MBProgressHUD to your project.

1. Add a pod entry for MBProgressHUD to your Podfile `pod 'MBProgressHUD', '~> 1.0.0'`
2. Install the pod(s) by running `pod install`.
3. Include MBProgressHUD wherever you need it with `#import "MBProgressHUD.h"`.

### Carthage

1. Add MBProgressHUD to your Cartfile. e.g., `github "jdg/MBProgressHUD" ~> 1.0.0`
2. Run `carthage update`
3. Follow the rest of the [standard Carthage installation instructions](https://github.com/Carthage/Carthage#adding-frameworks-to-an-application) to add MBProgressHUD to your project.

### Source files

Alternatively you can directly add the `MBProgressHUD.h` and `MBProgressHUD.m` source files to your project.

1. Download the [latest code version](https://github.com/matej/MBProgressHUD/archive/master.zip) or add the repository as a git submodule to your git-tracked project.
2. Open your project in Xcode, then drag and drop `MBProgressHUD.h` and `MBProgressHUD.m` onto your project (use the "Product Navigator view"). Make sure to select Copy items when asked if you extracted the code archive outside of your project.
3. Include MBProgressHUD wherever you need it with `#import "MBProgressHUD.h"`.

### Static library

You can also add MBProgressHUD as a static library to your project or workspace.

1. Download the [latest code version](https://github.com/matej/MBProgressHUD/downloads) or add the repository as a git submodule to your git-tracked project.
2. Open your project in Xcode, then drag and drop `MBProgressHUD.xcodeproj` onto your project or workspace (use the "Product Navigator view").
3. Select your target and go to the Build phases tab. In the Link Binary With Libraries section select the add button. On the sheet find and add `libMBProgressHUD.a`. You might also need to add `MBProgressHUD` to the Target Dependencies list.
4. Include MBProgressHUD wherever you need it with `#import <MBProgressHUD/MBProgressHUD.h>`.

## 使用举例

在需要等待的时候, 可以使用 showWait, 代码及效果如下:

```swift
SwiftProgressHUD.showWait()

/// 模拟 1s后 加载完成
DispatchQueue.main.asyncAfter(deadline: .now() + 1) {
SwiftProgressHUD.hideAllHUD()
}
```
加载成功时, 提示可以使用showSuccess, 代码及效果如下:

```swift
SwiftProgressHUD.showSuccess("加载成功")

/// 模拟 1s后 加载完成
DispatchQueue.main.asyncAfter(deadline: .now() + 1) {
SwiftProgressHUD.hideAllHUD()
}
```
加载失败时, 提示可以使用showFail, 代码及效果如下:

```swift
SwiftProgressHUD.showFail("加载失败")

/// 模拟 1s后 加载完成
DispatchQueue.main.asyncAfter(deadline: .now() + 1) {
SwiftProgressHUD.hideAllHUD()
}
```

友情提示信息, 可以使用showInfo, 代码及效果如下:

```swift
SwiftProgressHUD.showInfo("请稍后")

/// 模拟 1s后 加载完成
DispatchQueue.main.asyncAfter(deadline: .now() + 1) {
SwiftProgressHUD.hideAllHUD()
}
```

错误Toast提示信息, 可以使用, 代码及效果如下:

```swift
SwiftProgressHUD.showOnlyText("请输入合法的手机号")

/// 模拟 1s后 加载完成
DispatchQueue.main.asyncAfter(deadline: .now() + 1) {
SwiftProgressHUD.hideAllHUD()
}
```



The main guideline you need to follow when dealing with MBProgressHUD while running long-running tasks is keeping the main thread work-free, so the UI can be updated promptly. The recommended way of using MBProgressHUD is therefore to set it up on the main thread and then spinning the task, that you want to perform, off onto a new thread.

```objective-c
[MBProgressHUD showHUDAddedTo:self.view animated:YES];
dispatch_async(dispatch_get_global_queue( DISPATCH_QUEUE_PRIORITY_LOW, 0), ^{
// Do something...
dispatch_async(dispatch_get_main_queue(), ^{
[MBProgressHUD hideHUDForView:self.view animated:YES];
});
});
```

You can add the HUD on any view or window. It is however a good idea to avoid adding the HUD to certain `UIKit` views with complex view hierarchies - like `UITableView` or `UICollectionView`. Those can mutate their subviews in unexpected ways and thereby break HUD display. 

If you need to configure the HUD you can do this by using the MBProgressHUD reference that showHUDAddedTo:animated: returns.

```objective-c
MBProgressHUD *hud = [MBProgressHUD showHUDAddedTo:self.view animated:YES];
hud.mode = MBProgressHUDModeAnnularDeterminate;
hud.labelText = @"Loading";
[self doSomethingInBackgroundWithProgressCallback:^(float progress) {
hud.progress = progress;
} completionCallback:^{
[hud hide:YES];
}];
```

You can also use a `NSProgress` object and MBProgressHUD will update itself when there is progress reported through that object.

```objective-c
MBProgressHUD *hud = [MBProgressHUD showHUDAddedTo:self.view animated:YES];
hud.mode = MBProgressHUDModeAnnularDeterminate;
hud.labelText = @"Loading";
NSProgress *progress = [self doSomethingInBackgroundCompletion:^{
[hud hide:YES];
}];
hud.progressObject = progress;
```

UI updates should always be done on the main thread. Some MBProgressHUD setters are however considered "thread safe" and can be called from background threads. Those also include `setMode:`, `setCustomView:`, `setLabelText:`, `setLabelFont:`, `setDetailsLabelText:`, `setDetailsLabelFont:` and `setProgress:`.

If you need to run your long-running task in the main thread, you should perform it with a slight delay, so UIKit will have enough time to update the UI (i.e., draw the HUD) before you block the main thread with your task.

```objective-c
[MBProgressHUD showHUDAddedTo:self.view animated:YES];
dispatch_time_t popTime = dispatch_time(DISPATCH_TIME_NOW, 0.01 * NSEC_PER_SEC);
dispatch_after(popTime, dispatch_get_main_queue(), ^(void){
// Do something...
[MBProgressHUD hideHUDForView:self.view animated:YES];
});
```

You should be aware that any HUD updates issued inside the above block won't be displayed until the block completes.

For more examples, including how to use MBProgressHUD with asynchronous operations such as NSURLConnection, take a look at the bundled demo project. Extensive API documentation is provided in the header file (MBProgressHUD.h).


## License

This code is distributed under the terms and conditions of the [MIT license](LICENSE).

## Change-log

A brief summary of each MBProgressHUD release can be found in the [CHANGELOG](CHANGELOG.mdown). 

