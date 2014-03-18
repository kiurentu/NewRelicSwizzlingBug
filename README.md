NewRelicSwizzlingBug
====================

Triggers a bug in New Relic's swizzling of `UIViewController`'s `viewDidLoad` method in iOS.

A bug in the swizzle implementation in New Relic's library found in v3.256 and potentially previous ones too.

A chain of subclasses where some of them don't implement `viewDidLoad` will trigger multiple calls to `viewDidLoad` in the base classes.

In this example we have `UIViewController`>`WHIViewController`>`WHIIntermediateViewController`>`WHIFinalViewController`.<br>
All of them implement `viewDidLoad`
![Example 1](http://f.cl.ly/items/1S3C2H432A39021Z2u3h/Screen%20Shot%202014-03-18%20at%2012.17.01%20PM.png)

In this example we have `UIViewController`>`WHIViewController`>`WHIIntermediateViewController`>`WHIFinalViewController`.<br>
All of them implement `viewDidLoad` except for `WHIIntermediateViewController`, so `WHIViewController`'s `viewDidLoad` is called twice.
![Example 2](http://f.cl.ly/items/313X2H2n3z0j1A3k150b/Screen%20Shot%202014-03-18%20at%2012.17.29%20PM.png)
