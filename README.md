# GradientSlider
![alt tag](https://cloud.githubusercontent.com/assets/167242/9134671/522e2f8a-3cbb-11e5-9d38-a0f1064a3e43.png)

GradientSlider is a UIControl subclass which is similar to UISlider, but with a linear gradient coloring the slider’s track. Useful for creating color pickers. It is written in Swift 2 and requires it.

**Features**
- Easily define a gradient by setting the min & max (i.e. left & right) colors
- Rainbow gradients (with customizable saturation & brightness) for making Hue selection sliders
- IBDesignable/Inspectable for direct use within Interface Builder
- Add an icon or color to the slider thumb
- Min/Max images (similar to UISlider)
- Both Target/Action and Block-based callbacks
- Customizable track thickness
- Customizable track border and thumb size
- Looks like UISlider by default, so they can be intermixed in the UI

## Installation
Drag the “UIGradientSlider” file into your Xcode project

## Usage via Interface Builder
Drag a custom view into your storyboard and change it’s class to “UIGradientSlider”. Use the attributes inspector to optionally set the slider’s basic properties:
- min/max color
- hasRainbow (Note: the min color’s saturation & brightness are used)
- value
- minimum/maximum value
- minimum/maximum images
- thickness
- thumbIcon

## Setting the Track Gradient Programmatically
### Min/Max Color
The track displays a linear gradient with the minColor corresponding to the minimumValue and the maxColor corresponding to the maximumValue. 

	slider.minValue = [UIColor blueColor];
	slider.maxValue = [UIColor orangeColor];

![img alt](https://cloud.githubusercontent.com/assets/167242/9134778/8c34e16e-3cbc-11e5-9c54-452e8d3a2af7.png)

### Rainbow
When the `hasRainbow` property is set to true, the track displays a rainbow gradient which moves around the color wheel (starting and ending with red). The saturation & brightness are both pulled from the color in `minValue`.

	slider.minValue = [UIColor blueColor]; //This has full saturation & brightness
	slider.hasRainbow = YES;

![img alt](https://cloud.githubusercontent.com/assets/167242/9134881/5269de02-3cbd-11e5-9d78-056aca2b42d9.png)


## Responding to User Interaction
### Target/Action
As a UIControl subclass, the traditional target/action approach is fully supported. The slider will send TouchDown, ValueChanged, and TouchUpInside actions. If the `continuous` property is set to true (which it is by default), then the slider will send ValueChanged actions as the slider changes, otherwise a ValueChanged action is only sent when the user releases the slider.

### ActionBlock
The slider will also call it’s actionBlock when its value is changed. If the `continuous` property is set to true (which it is by default), then the slider will call its actionBlock as the slider changes, otherwise it will only call it once when the slider is released.
The `actionBlock` property takes a closure which takes 2 parameters: The slider being changed and the new value, and has no return value. 
It’s signature is: `(UIGradientSlider,CGFloat)->()`


Images showing the effect of dragging the hue slider
![img alt](https://cloud.githubusercontent.com/assets/167242/9134674/55ae1c60-3cbb-11e5-888b-515dfc76898a.png)

![img alt](https://cloud.githubusercontent.com/assets/167242/9134675/57c3043e-3cbb-11e5-8fa6-71b0f55b1105.png)

## Customizing the Track
Besides the background gradient, the track is customizable in several ways using the following properties:
- `thickness:CGFloat` This sets the track’s thickness. The default value is 2pts
- `borderColor:UIColor` This sets the color of the track’s border. The default value is black.
- `borderWidth:CGFloat` This sets the width of the track’s border. The default value is 0 (i.e. no border).
- `minimumValueImage:UIImage` This places an image to the left of the track. Setting it to nil removes any image which is there. The default value is nil (i.e. no image).
- `maximumValueImage:UIImage` This places an image to the right of the track. Setting it to nil removes any image which is there. The default value is nil (i.e. no image). 
- `trackBorderWidth:CGFloat` This sets the border width for track(slider).
- `trackBorderColor:UIColor` This sets the border color for track(slider).
	 
## Customizing the Thumb
The thumb can be resized, given a custom color or an icon (it can not have both a color and an icon at the same time). To customize the thumb, use the following properties:
- `thumbSize:CGFloat` This sets the diameter of the thumb. Note: Resizing the thumb may change the slider’s intrisicContentSize. The default is 28.0 pts.
- `thumbColor:UIColor` This sets the color displayed by the thumb. When the thumb has an associated icon, the color is automatically set to clearColor, and setting a new color removes the icon. The default value is White.
- `thumbIcon:UIImage` This sets the image to display inside the slider’s thumb. Setting an image automatically removes the thumbColor, and setting a color removes the icon. The default value is nil (i.e. no image)
- `thumbBorderColor:UIColor` This sets the border color for thumb.
- `thumbBorderWidth:CGFloat` This sets the border width for thumb.

## License
The MIT License (MIT)

Copyright (c) 2017 Vasily Popov

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
