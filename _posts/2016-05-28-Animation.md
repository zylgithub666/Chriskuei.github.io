---
title: Animation
layout: post
description: Make your animations look more realistic
---

> Make your animations look more realistic

## animateWithDuration

- **duration:** The duration of the animation.
- **delay:** The amount of seconds UIKit will wait before it starts the animation.
- **options:** A set of animation options allowing you to customize a number of aspects about your animation. You’ll learn more about this parameter later on, but for now you can pass [] to mean “no options.”
- **animations:** The closure expression to provide your animations.
- **completion:** A code closure to execute when the animation completes; this parameter often comes in handy when you want to perform some final cleanup tasks or chain animations one after the other.


```swift
UIView.animateWithDuration(0.5, delay: 0.4, options: [], animations: {
  self.password.center.x += self.view.bounds.width
}, completion: nil)
```



## Bounds & Frame

- The bounds of an UIView is the rectangle, expressed as a location (x,y) and size (width,height) relative to its **own coordinate system (0,0)**.


- The frame of an UIView is the rectangle, expressed as a location (x,y) and size (width,height) relative to **the superview it is contained within**.



## Animatable properties

### Position and size

- **bounds:** Animate this property to reposition the view’s content within the view’s frame.


- **frame:** Animate this property to move and/or scale the view.


- **center:** Animate this property when you want to move the view to a new location on screen.

### Appearance

- **backgroundColor:** Change this property of a view to have UIKit gradually change the tint of the background color over time.
- **alpha:** Change this property to create fade-in and fade-out effects.

### Transformation

- **transform:** modify this property within an animation block to animate the rotation, scale, and/or position of a view.



## Animation options

### Repeating

- **.Repeat:** Include this option to makes your animation loop forever.
- **.Autoreverse:**Include this option only in conjunction with **.Repeat**; this option repeatedly plays your animation in forward then in reverse.

```swift
UIView.animateWithDuration(0.5, delay: 0.4,
  options: .Repeat, animations: {
  self.password.center.x += self.view.bounds.width
}, completion: nil)
```

### Animation easing

#### Easing options

- **.Linear:** This option applies no acceleration or deceleration to the animation.
- **.CurveEaseIn:** This option applies acceleration to the start of your animation.
- **.CurveEaseOut:** This option applies deceleration to the end of your animation.
- **.CurveEaseInOut:** This option applies acceleration to the start of your animation and applies deceleration to the end of your animation.

```swi
UIView.animateWithDuration(0.5, delay: 0.4,
  options: [.Repeat, .Autoreverse, .CurveEaseOut], animations: {
    self.password.center.x += self.view.bounds.width
}, completion: nil)
```



## Spring animations

`animateWithDuration(_:delay:usingSpringWithDamping:initialSpringVelocity:options:animations:completion:)`

- **usingSpringWithDamping:** This controls the amount of damping, or reduction, applied to the animation as it approaches its final state.. This parameter accepts values between 0.0 and 1.0. Values closer to 0.0 create a bouncier animation, while values closer to 1.0 create a stiff-looking effect. You can think of this value as the "stiffness" of the spring.
- **initialSpringVelocity:** This controls the initial velocity of the animation. A value of 1.0 sets the velocity of the animation to cover the total distance of the animation in the span of one second. Bigger and smaller values will cause the animation to have more or less velocity.

```swift
 UIView.animateWithDuration(0.5, delay: 0.5, usingSpringWithDamping: 0.5, initialSpringVelocity: 0.0, options: [], animations: {
            self.loginButton.center.y -= 30.0
            self.loginButton.alpha = 1.0
            }, completion: nil)
```



## Animating user interactions

You don't have to limit your spring animations to the initial placement of your views. In fact, animating views in response to user input can really make your interface come alive.



## Transitions

### Example transitions

####Transition animation options:

- .TransitionFlipFromLeft
- .TransitionFlipFromRight
- .TransitionCurlUp
- .TransitionCurlDown
- .TransitionCrossDissolve
- .TransitionFlipFromTop
- .TransitionFlipFromBottom

#### transitionWithView

- Adding a new view: `self.view.addSubview(newView)`
- Removing a view: `self.newView.removeFromSuperview()`
- Hiding/Showing a view: `self.newView.hidden = true`
- Replacing a view with another view:`UIView.transitionFromView(self.oldView!, toView: self.newVIew!, duration: 0.33, options: [.TransitionFlipFromTop], completion: nil)




## animateKeyframesWithDuration

```swift
UIView.animateKeyframesWithDuration(1.5, delay: 0.0, options: [], animations: {

    UIView.addKeyframeWithRelativeStartTime(0.0, relativeDuration: 0.25, animations: {
        self.planeImage.center.x += 80.0
        self.planeImage.center.y -= 10.0
    })

    UIView.addKeyframeWithRelativeStartTime(0.1, relativeDuration: 0.4, animations: {
        self.planeImage.transform = CGAffineTransformMakeRotation(CGFloat(-M_PI_4/2))
    })

    UIView.addKeyframeWithRelativeStartTime(0.25, relativeDuration: 0.25, animations: {
        self.planeImage.center.x += 100.0
        self.planeImage.center.y -= 50.0
        self.planeImage.alpha = 0.0
    })
    UIView.addKeyframeWithRelativeStartTime(0.51, relativeDuration: 0.01, animations: {
        self.planeImage.transform = CGAffineTransformIdentity
        self.planeImage.center = CGPoint(x: 0.0, y: originalCenter.y)
    })
    UIView.addKeyframeWithRelativeStartTime(0.55, relativeDuration: 0.45, animations: {
        self.planeImage.alpha = 1.0
        self.planeImage.center = originalCenter
    })
    }, completion: nil)
```



## Auto Layout Constaints

### Animating Constraints

- use **layoutIfNeeded**

  ```swift
  [UIView.animateWithDuration(1.0, delay: 0.0, usingSpringWithDamping: 0.4, initialSpringVelocity: 10.0, options: .CurveEaseIn, animations: {
    self.view.layoutIfNeeded()
    }, completion: nil)
  ```

- Rotate views by adjusting their `transform`

  ```swift
  let angle = self.isMenuOpen ? CGFloat(M_PI_4) : 0.0
              self.buttonMenu.transform = CGAffineTransformMakeRotation(angle)
  ```

  ​
