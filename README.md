# LGSideMenuController

iOS view controller, shows left and right views by pressing button or gesture.

[![Platform](https://img.shields.io/cocoapods/p/LGSideMenuController.svg)](https://github.com/Friend-LGA/LGSideMenuController)
[![CocoaPods](https://img.shields.io/cocoapods/v/LGSideMenuController.svg)](http://cocoadocs.org/docsets/LGSideMenuController)
[![Carthage](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg)](https://github.com/Friend-LGA/LGSideMenuController)
[![License](http://img.shields.io/cocoapods/l/LGSideMenuController.svg)](https://raw.githubusercontent.com/Friend-LGA/LGSideMenuController/master/LICENSE)

## Preview

<img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/Preview1.gif" width="285"/> <img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/1.png" width="286"/> <img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/2.png" width="286"/>
<img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/Preview2.gif" width="285"/>  <img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/3.png" width="286"/> <img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/4.png" width="286"/>
<img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/Preview3.gif" width="285"/> <img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/5.png" width="286"/> <img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/6.png" width="286"/>

## Installation

| LGSideMenuController version | iOS version |
|------------------------------|-------------|
| <= 1.0.10                    | >= 6.0      |
| >= 1.1.0                     | >= 8.0      |

### With source code

[Download repository](https://github.com/Friend-LGA/LGSideMenuController/archive/master.zip), then add [LGSideMenuController directory](https://github.com/Friend-LGA/LGSideMenuController/blob/master/LGSideMenuController/) to your project.

Then import header files where you need to use the library

##### Objective-C

```objective-c
#import "LGSideMenuController.h"
#import "UIViewController+LGSideMenuController.h"
```

##### Swift

For swift you need to create [bridging header](https://developer.apple.com/library/content/documentation/Swift/Conceptual/BuildingCocoaApps/MixandMatch.html)

```objective-c
// BridgingHeader.h
#import "LGSideMenuController.h"
#import "UIViewController+LGSideMenuController.h"
```

### With CocoaPods

CocoaPods is a dependency manager for Objective-C, which automates and simplifies the process of using 3rd-party libraries in your projects. To install with cocoaPods, follow the "Get Started" section on [CocoaPods](https://cocoapods.org/).

#### Podfile

```ruby
platform :ios, '8.0'
use_frameworks!
pod 'LGSideMenuController'
```

Then import framework where you need to use the library

##### Objective-C

```objective-c
#import <LGSideMenuController/LGSideMenuController.h>
#import <LGSideMenuController/UIViewController+LGSideMenuController.h>
// OR
@import LGSideMenuController;
// OR
@import LGSideMenuController.LGSideMenuController;
@import LGSideMenuController.UIViewController_LGSideMenuController;
```

##### Swift

```swift
import LGSideMenuController
// OR
import LGSideMenuController.LGSideMenuController
import LGSideMenuController.UIViewController_LGSideMenuController
```

### With Carthage

Carthage is a lightweight dependency manager for Swift and Objective-C. It leverages CocoaTouch modules and is less invasive than CocoaPods. To install with carthage, follow the instruction on [Carthage](https://github.com/Carthage/Carthage/).

#### Cartfile

```ruby
github "Friend-LGA/LGSideMenuController"
```

Then import framework where you need to use the library

##### Objective-C

```objective-c
#import <LGSideMenuController/LGSideMenuController.h>
#import <LGSideMenuController/UIViewController+LGSideMenuController.h>
// OR
@import LGSideMenuController;
// OR
@import LGSideMenuController.LGSideMenuController;
@import LGSideMenuController.UIViewController_LGSideMenuController;
```

##### Swift

```swift
import LGSideMenuController
// OR
import LGSideMenuController.LGSideMenuController
import LGSideMenuController.UIViewController_LGSideMenuController
```

## Usage

### Initialization

You can use view controllers or views to initialize LGSideMenuController:

##### Objective-C

```objective-c
- (nonnull instancetype)initWithRootViewController:(nullable UIViewController *)rootViewController;

- (nonnull instancetype)initWithRootViewController:(nullable UIViewController *)rootViewController
                                leftViewController:(nullable UIViewController *)leftViewController
                               rightViewController:(nullable UIViewController *)rightViewController;

- (nonnull instancetype)initWithRootView:(nullable UIView *)rootView;

- (nonnull instancetype)initWithRootView:(nullable UIView *)rootView
                                leftView:(nullable UIView *)leftView
                               rightView:(nullable UIView *)rightView;
```

##### Swift

```swift
public init(rootViewController: UIViewController?)

public init(rootViewController: UIViewController?,
            leftViewController: UIViewController?,
           rightViewController: UIViewController?)

public init(rootView: UIView?)

public init(rootView: UIView?,
            leftView: UIView?,
           rightView: UIView?)
```

### Setup

To set or to change root, left or right view controllers or views, call:

```swift
sideMenuController.rootViewController = rootViewController
sideMenuController.leftViewController = leftViewController
sideMenuController.rightViewController = rightViewController

sideMenuController.rootView = rootView
sideMenuController.leftView = leftView
sideMenuController.rightView = rightView
```

If you set, for example, `sideMenuController.rootViewController = rootViewController`,
then `sideMenuController.rootView == rootViewController.view`.    
If you have, for example, `sideMenuController.rootViewController != nil` and you set `sideMenuController.rootView = rootView`, then `sideMenuController.rootViewController == nil`.

### Quick Example

##### Objective-C

```objective-c
UIViewController *rootViewController = [UIViewController new];
UITableViewController *leftViewController = [UITableViewController new];
UITableViewController *rightViewController = [UITableViewController new];

UINavigationController *navigationController = [[UINavigationController alloc] initWithRootViewController:rootViewController];

LGSideMenuController *sideMenuController = [LGSideMenuController sideMenuControllerWithRootViewController:navigationController
                                                                                       leftViewController:leftViewController
                                                                                      rightViewController:rightViewController];

sideMenuController.leftViewWidth = 250.0;
sideMenuController.leftViewPresentationStyle = LGSideMenuPresentationStyleScaleFromBig;

sideMenuController.rightViewWidth = 100.0;
sideMenuController.leftViewPresentationStyle = LGSideMenuPresentationStyleSlideBelow;
```

##### Swift

```swift
let rootViewController = UIViewController()
let leftViewController = UITableViewController()
let rightViewController = UITableViewController()

let navigationController = UINavigationController(rootViewController: rootViewController)

let sideMenuController = LGSideMenuController(rootViewController: navigationController,
                                              leftViewController: leftViewController,
                                             rightViewController: rightViewController)

sideMenuController.leftViewWidth = 250.0;
sideMenuController.leftViewPresentationStyle = .scaleFromBig;

sideMenuController.rightViewWidth = 100.0;
sideMenuController.leftViewPresentationStyle = .slideBelow;
```

For better examples check demo projects.

### Blur

You can use UIBlurEffect with next properties:

```objective-c
UIBlurEffect *leftViewBackgroundBlurEffect;
UIBlurEffect *rightViewBackgroundBlurEffect;

UIBlurEffect *rootViewCoverBlurEffectForLeftView;
UIBlurEffect *rootViewCoverBlurEffectForRightView;

UIBlurEffect *leftViewCoverBlurEffect;
UIBlurEffect *rightViewCoverBlurEffect;
```

For example:

##### Objective-C

```objective-c
sideMenuController.leftViewBackgroundBlurEffect = [UIBlurEffect effectWithStyle:UIBlurEffectStyleRegular];
```

##### Swift

```swift
sideMenuController.leftViewBackgroundBlurEffect = UIBlurEffect(style: .regular)
```

If you want to change color of blurred view, use:

```objective-c
UIColor *leftViewBackgroundColor;
UIColor *rightViewBackgroundColor;

UIColor *rootViewCoverColorForLeftView;
UIColor *rootViewCoverColorForRightView;

UIColor *leftViewCoverColor;
UIColor *rightViewCoverColor;
```

For example:

##### Objective-C

```objective-c
sideMenuController.leftViewBackgroundColor = [UIColor colorWithRed:0.0 green:0.5 blue:1.0 alpha:0.1];
```

##### Swift

```swift
sideMenuController.leftViewBackgroundColor = UIColor(red: 0.0, green: 0.5, blue: 1.0, alpha: 0.1)
```

If you want to change intensity of blurred view, use:

```objective-c
CGFloat leftViewBackgroundAlpha;
CGFloat rightViewBackgroundAlpha;

CGFloat rootViewCoverAlphaForLeftView;
CGFloat rootViewCoverAlphaForRightView;

CGFloat CGFloatleftViewCoverAlpha;
CGFloat rightViewCoverAlpha;
```

For example:

```objective-c
sideMenuController.leftViewBackgroundAlpha = 0.9;
```

### Status Bar

You can't use `prefersStatusBarHidden, preferredStatusBarStyle, preferredStatusBarUpdateAnimation`,
instead you need to override all these methods for each controller separated, or use properties of sideMenuController:

```objective-c
BOOL rootViewStatusBarHidden;
UIStatusBarStyle rootViewStatusBarStyle;
UIStatusBarAnimation rootViewStatusBarUpdateAnimation;

BOOL leftViewStatusBarHidden;
UIStatusBarStyle leftViewStatusBarStyle;
UIStatusBarAnimation leftViewStatusBarUpdateAnimation;

BOOL rightViewStatusBarHidden;
UIStatusBarStyle rightViewStatusBarStyle;
UIStatusBarAnimation rightViewStatusBarUpdateAnimation;
```

And these properties have greater priority then overridden `prefersStatusBarHidden, preferredStatusBarStyle, preferredStatusBarUpdateAnimation`.

For example, you had sideMenuController with rootViewController, leftViewController and rightViewController.
For rootViewController, you can override it's default methods or use sideMenuController's properties:

##### Objective-C

```objective-c
// In RootViewController.m

- (BOOL)prefersStatusBarHidden {
    return NO;
}

- (UIStatusBarStyle)preferredStatusBarStyle {
    return UIStatusBarStyleDefault;
}

- (UIStatusBarAnimation)preferredStatusBarUpdateAnimation {
    return UIStatusBarAnimationNone;
}

// OR in SideMenuController.m

self.rootViewStatusBarHidden = NO;
self.rootViewStatusBarStyle = UIStatusBarStyleDefault;
self.rootViewStatusBarUpdateAnimation = UIStatusBarAnimationNone;

// OR

- (BOOL)isRootViewStatusBarHidden {
    return NO;
}

- (UIStatusBarStyle)rootViewStatusBarStyle {
    return UIStatusBarStyleDefault;
}

- (UIStatusBarAnimation)rootViewStatusBarUpdateAnimation {
    return UIStatusBarAnimationNone;
}
```

##### Swift

```swift
// In RootViewController.swift

override var prefersStatusBarHidden : Bool {
    return false
}

override var preferredStatusBarStyle : UIStatusBarStyle {
    return .default
}

override var preferredStatusBarUpdateAnimation : UIStatusBarAnimation {
    return .none
}

// OR in SideMenuController.swift

rootViewStatusBarHidden = false
rootViewStatusBarStyle = .default
rootViewStatusBarUpdateAnimation = .none

// OR

override var isRootViewStatusBarHidden : Bool {
    get { return false }
    set { super.isRootViewStatusBarHidden = newValue }
}

override var rootViewStatusBarStyle : UIStatusBarStyle {
    get { return .default }
    set { super.rootViewStatusBarStyle = newValue }
}

override var rootViewStatusBarUpdateAnimation : UIStatusBarAnimation {
    get { return .none }
    set { super.rootViewStatusBarUpdateAnimation = newValue }
}
```

For `leftViewController and rightViewController` principe the same, but lets look at situation, when animations are different for each viewController.    
* When side views are hidden, then `statusBarUpdateAnimation == rootViewController.statusBarUpdateAnimation`.    
* When left view is going to show, then `statusBarUpdateAnimation == leftViewController.statusBarUpdateAnimation`.    
* When left view is going to hide and root view is going to show, then `statusBarUpdateAnimation == rootViewController.statusBarUpdateAnimation`.

But may be you want to `statusBarUpdateAnimation == leftViewController.statusBarUpdateAnimation` also when left view is going to hide.    
Then you can do next:

##### Objective-C

```objective-c
// In RootViewController.m

- (UIStatusBarAnimation)preferredStatusBarUpdateAnimation {
    if (self.sideMenuController.isLeftViewVisible) {
        return UIStatusBarAnimationFade;
    }
    else if (self.sideMenuController.isRightViewVisible) {
        return UIStatusBarAnimationSlide;
    }
    else {
        return UIStatusBarAnimationNone;
    }
}

// OR in SideMenuController.m

- (UIStatusBarAnimation)rootViewStatusBarUpdateAnimation {
    if (self.isLeftViewVisible) {
        return UIStatusBarAnimationFade;
    }
    else if (self.isRightViewVisible) {
        return UIStatusBarAnimationSlide;
    }
    else {
        return UIStatusBarAnimationNone;
    }
}
```

##### Swift

```swift
// In RootViewController.swift

override var preferredStatusBarUpdateAnimation : UIStatusBarAnimation {
    if sideMenuController.isLeftViewVisible {
        return UIStatusBarAnimationFade
    }
    else if sideMenuController.isRightViewVisible {
        return UIStatusBarAnimationSlide
    }
    else {
        return UIStatusBarAnimationNone
    }
}

// OR in SideMenuController.swift

override var rootViewStatusBarUpdateAnimation : UIStatusBarAnimation {
    get {
        if isLeftViewVisible {
            return UIStatusBarAnimationFade
        }
        else if isRightViewVisible {
            return UIStatusBarAnimationSlide
        }
        else {
            return UIStatusBarAnimationNone
        }
    }

    set { super.rootViewStatusBarUpdateAnimation = newValue }
}
```

### Always visible options

Sometimes, for example on iPad, you need to have toggleable side menu on portrait orientation and always visible side menu on landscape orientation

You can get it with properties:

```objective-c
LGSideMenuAlwaysVisibleOptions leftViewAlwaysVisibleOptions;
LGSideMenuAlwaysVisibleOptions rightViewAlwaysVisibleOptions;
```

LGSideMenuAlwaysVisibleOptions has values:

```
LGSideMenuAlwaysVisibleOnNone
LGSideMenuAlwaysVisibleOnLandscape
LGSideMenuAlwaysVisibleOnPortrait
LGSideMenuAlwaysVisibleOnPad
LGSideMenuAlwaysVisibleOnPhone
LGSideMenuAlwaysVisibleOnPadLandscape
LGSideMenuAlwaysVisibleOnPadPortrait
LGSideMenuAlwaysVisibleOnPhoneLandscape
LGSideMenuAlwaysVisibleOnPhonePortrait
LGSideMenuAlwaysVisibleOnAll
```

You can choose multiple values like this:

##### Objective-C

```objective-c
sideMenuController.leftViewAlwaysVisibleOptions = LGSideMenuAlwaysVisibleOnPadLandscape|LGSideMenuAlwaysVisibleOnPhoneLandscape;
```

##### Swift

```swift
sideMenuController.leftViewAlwaysVisibleOptions = [.onPadLandscape, .onPhoneLandscape]
```

### NavigationController's back gesture

Back gesture for UINavigationController has greater priority then swipe gesture for LGSideMenuController.
But if you want, you can disable `interactivePopGestureRecognizer`, or change `swipeGestureArea`, or increase `leftViewSwipeGestureRange, rightViewSwipeGestureRange`.

##### Objective-C

```objective-c
navigationController.interactivePopGestureRecognizer.enabled = NO;

// OR

sideMenuController.swipeGestureArea = LGSideMenuSwipeGestureAreaFull;

// OR

sideMenuController.leftViewSwipeGestureRange = LGSideMenuSwipeGestureRangeMake(44.0, 88.0);
sideMenuController.rightViewSwipeGestureRange = LGSideMenuSwipeGestureRangeMake(88.0, 44.0);
```

##### Swift

```swift
navigationController.interactivePopGestureRecognizer.isEnabled = false

// OR

sideMenuController.swipeGestureArea = .full

// OR

sideMenuController.leftViewSwipeGestureRange = LGSideMenuSwipeGestureRangeMake(44.0, 88.0)
sideMenuController.rightViewSwipeGestureRange = LGSideMenuSwipeGestureRangeMake(88.0, 44.0)
```

### Editable Table View

If you have editable table view inside sideMenuController, then it will work fine if you swipe rows not inside `swipeGestureArea` for sideMenuController.
If you need more place for swipe inside table view, then you can decrease `leftViewSwipeGestureRange, rightViewSwipeGestureRange` or disable it.

##### Objective-C

```objective-c
sideMenuController.swipeGestureArea = LGSideMenuSwipeGestureAreaBorders; // Default

sideMenuController.leftViewSwipeGestureRange = LGSideMenuSwipeGestureRangeMake(44.0, 32.0);
sideMenuController.rightViewSwipeGestureRange = LGSideMenuSwipeGestureRangeMake(32.0, 44.0);

// OR

sideMenuController.leftViewSwipeGestureEnabled = NO;
sideMenuController.rightViewSwipeGestureEnabled = NO;
```

##### Swift

```swift
sideMenuController.swipeGestureArea = .borders // Default

sideMenuController.leftViewSwipeGestureRange = LGSideMenuSwipeGestureRangeMake(44.0, 32.0)
sideMenuController.rightViewSwipeGestureRange = LGSideMenuSwipeGestureRangeMake(32.0, 44.0)

// OR

sideMenuController.leftViewSwipeGestureEnabled = false
sideMenuController.rightViewSwipeGestureEnabled = false
```

### Storyboard

Almost all properties you can set right inside storyboard:

<img src="https://raw.githubusercontent.com/Friend-LGA/ReadmeFiles/master/LGSideMenuController/StoryboardProperties.png" width="244"/>

### Handle actions

To handle actions you can use delegate, blocks or notifications:

#### Delegate

##### Objective-C

```objective-c
<LGSideMenuControllerDelegate>

@optional

- (void)willShowLeftView:(nonnull UIView *)leftView sideMenuController:(nonnull LGSideMenuController *)sideMenuController;
- (void)didShowLeftView:(nonnull UIView *)leftView sideMenuController:(nonnull LGSideMenuController *)sideMenuController;

- (void)willHideLeftView:(nonnull UIView *)leftView sideMenuController:(nonnull LGSideMenuController *)sideMenuController;
- (void)didHideLeftView:(nonnull UIView *)leftView sideMenuController:(nonnull LGSideMenuController *)sideMenuController;

- (void)willShowRightView:(nonnull UIView *)rightView sideMenuController:(nonnull LGSideMenuController *)sideMenuController;
- (void)didShowRightView:(nonnull UIView *)rightView sideMenuController:(nonnull LGSideMenuController *)sideMenuController;

- (void)willHideRightView:(nonnull UIView *)rightView sideMenuController:(nonnull LGSideMenuController *)sideMenuController;
- (void)didHideRightView:(nonnull UIView *)rightView sideMenuController:(nonnull LGSideMenuController *)sideMenuController;

- (void)showAnimationsBlockForLeftView:(nonnull UIView *)leftView sideMenuController:(nonnull LGSideMenuController *)sideMenuController duration:(NSTimeInterval)duration;
- (void)hideAnimationsBlockForLeftView:(nonnull UIView *)leftView sideMenuController:(nonnull LGSideMenuController *)sideMenuController duration:(NSTimeInterval)duration;

- (void)showAnimationsBlockForRightView:(nonnull UIView *)rightView sideMenuController:(nonnull LGSideMenuController *)sideMenuController duration:(NSTimeInterval)duration;
- (void)hideAnimationsBlockForRightView:(nonnull UIView *)rightView sideMenuController:(nonnull LGSideMenuController *)sideMenuController duration:(NSTimeInterval)duration;
```

##### Swift

```swift
<LGSideMenuControllerDelegate>

optional public func willShowLeftView(_ leftView: UIView, sideMenuController: LGSideMenuController)
optional public func didShowLeftView(_ leftView: UIView, sideMenuController: LGSideMenuController)

optional public func willHideLeftView(_ leftView: UIView, sideMenuController: LGSideMenuController)
optional public func didHideLeftView(_ leftView: UIView, sideMenuController: LGSideMenuController)

optional public func willShowRightView(_ rightView: UIView, sideMenuController: LGSideMenuController)
optional public func didShowRightView(_ rightView: UIView, sideMenuController: LGSideMenuController)

optional public func willHideRightView(_ rightView: UIView, sideMenuController: LGSideMenuController)
optional public func didHideRightView(_ rightView: UIView, sideMenuController: LGSideMenuController)

optional public func showAnimationsBlock(forLeftView leftView: UIView, sideMenuController: LGSideMenuController, duration: TimeInterval)
optional public func hideAnimationsBlock(forLeftView leftView: UIView, sideMenuController: LGSideMenuController, duration: TimeInterval)

optional public func showAnimationsBlock(forRightView rightView: UIView, sideMenuController: LGSideMenuController, duration: TimeInterval)
optional public func hideAnimationsBlock(forRightView rightView: UIView, sideMenuController: LGSideMenuController, duration: TimeInterval)
```

#### Blocks

##### Objective-C

```objective-c
void(^ _Nullable willShowLeftView)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull leftView);
void(^ _Nullable didShowLeftView)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull leftView);

void(^ _Nullable willHideLeftView)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull leftView);
void(^ _Nullable didHideLeftView)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull leftView);

void(^ _Nullable willShowRightView)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull rightView);
void(^ _Nullable didShowRightView)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull rightView);

void(^ _Nullable willHideRightView)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull rightView);
void(^ _Nullable didHideRightView)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull rightView);

void(^ _Nullable showLeftViewAnimationsBlock)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull leftView, NSTimeInterval duration);
void(^ _Nullable hideLeftViewAnimationsBlock)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull leftView, NSTimeInterval duration);

void(^ _Nullable showRightViewAnimationsBlock)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull rightView, NSTimeInterval duration);
void(^ _Nullable hideRightViewAnimationsBlock)(LGSideMenuController * _Nonnull sideMenuController, UIView * _Nonnull rightView, NSTimeInterval duration);
```

##### Swift

```swift
open var willShowLeftView: ((LGSideMenuController, UIView) -> Swift.Void)?
open var didShowLeftView: ((LGSideMenuController, UIView) -> Swift.Void)?

open var willHideLeftView: ((LGSideMenuController, UIView) -> Swift.Void)?
open var didHideLeftView: ((LGSideMenuController, UIView) -> Swift.Void)?

open var willShowRightView: ((LGSideMenuController, UIView) -> Swift.Void)?
open var didShowRightView: ((LGSideMenuController, UIView) -> Swift.Void)?

open var willHideRightView: ((LGSideMenuController, UIView) -> Swift.Void)?
open var didHideRightView: ((LGSideMenuController, UIView) -> Swift.Void)?

open var showLeftViewAnimationsBlock: ((LGSideMenuController, UIView, TimeInterval) -> Swift.Void)?
open var hideLeftViewAnimationsBlock: ((LGSideMenuController, UIView, TimeInterval) -> Swift.Void)?

open var showRightViewAnimationsBlock: ((LGSideMenuController, UIView, TimeInterval) -> Swift.Void)?
open var hideRightViewAnimationsBlock: ((LGSideMenuController, UIView, TimeInterval) -> Swift.Void)?
```

#### Notifications

```
LGSideMenuControllerWillShowLeftViewNotification
LGSideMenuControllerDidShowLeftViewNotification

LGSideMenuControllerWillHideLeftViewNotification
LGSideMenuControllerDidHideLeftViewNotification

LGSideMenuControllerWillShowRightViewNotification
LGSideMenuControllerDidShowRightViewNotification

LGSideMenuControllerWillHideRightViewNotification
LGSideMenuControllerDidHideRightViewNotification
```

### More

For more details see [header files](https://github.com/Friend-LGA/LGSideMenuController/tree/master/LGSideMenuController) and try Xcode demo projects:
* [Objective-C](https://github.com/Friend-LGA/LGSideMenuController/tree/master/Demo_Objective-C)
* [Objective-C + Storyboard](https://github.com/Friend-LGA/LGSideMenuController/tree/master/Demo_Objective-C_Storyboard)
* [Swift](https://github.com/Friend-LGA/LGSideMenuController/tree/master/Demo_Swift)
* [Swift + Storyboard](https://github.com/Friend-LGA/LGSideMenuController/tree/master/Demo_Swift_Storyboard)

## Xamarin

If you use Xamarin, look at this repository:
* https://github.com/yahavgb/LGSideMenuController-Xamarin

## Frameworks

If you like LGSideMenuController, check out my other useful libraries:
* [LGAlertView](https://github.com/Friend-LGA/LGAlertView)
  Customizable implementation of UIAlertViewController, UIAlertView and UIActionSheet. All in one. You can customize every detail. Make AlertView of your dream! :)
* [LGPlusButtonsView](https://github.com/Friend-LGA/LGPlusButtonsView)
  Customizable iOS implementation of Floating Action Button (Google Plus Button, fab).

## License

LGSideMenuController is released under the MIT license. See [LICENSE](https://raw.githubusercontent.com/Friend-LGA/LGSideMenuController/master/LICENSE) for details.
