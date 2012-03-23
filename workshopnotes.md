#@PPK - Mobile Web Workshop

###Misc Notes
- Adobe shadow, testing on multiple phone devices, currently for iOS & Android

Right now we have plenty of ideas but no one knows how to mix those ideas with the current knowledge we have from the desktop web.

###JavaScript Touch Events

Examples: http://quirksmode.org/touchevents

####Browser support:
(in order of goodness)

Remember, webkit is a _rendering engine_, not a browser.

- Safari on iPad / iPhone (best mobile browser right now)
- BlackBerry Webkit on OS6+ (excellent browser). OS5 and below was
  horrible.
- Samsung Dolfin on bada
- Opera Mobile 12 
- Android Webkit on Android 2.3 & 3, if a website works on Android, it
  will probably work fine on everything else.
- Firefox 10 on Android 3
- UC 8 on Android 2.3 (most popular browser in China)


####Touch Events
Supported by all above browsers
- touchstart
- touchmove
- touchend

####touchmove
- it's complicated to figure out whether the user has left ehe element
- what we need is `touchenter` and `touchleave` events that fire when the touch enters or leaves an element

####event info
- touches array: contans all current touches (up to a max of 11)
- changedTouches array: contains all touches that caused an event to fire
- targetTouches array: contains all touches on the target element
- `var currentTouch = event.touches[0]`

(best documentation is the Apple docs)

Find out if a user is on a touchscreen, see if the `ontouchstart` fires, and if it does, get rid of the `onmousedown` event, so you don't execute both of them at the same time (waste). The reverse of this __doesn't work__.

The mouse and touch events are equivalent. But they __are not__ the same.

Touch events give:
- area of click
- pressure (not there yet at all)
- multitouch

####Tricky Bits
- some devices fire two events simultaneously (Nokia E71, not touchscreen, fired mouse & keyboard events when navigating page).
- multitouch can't be ported to mouse & keyboard events
- on a touchscreen device the mouse events must also be supported, because too many websites depend on them. This leads to a cascade of events

####Event Cascade
When user touches touchscreen, these events fire:

- touchstart
- mouseover
- mousemove (one)
- mousedown
- mouseup
- click

It's not as big a problem as you'd think as in general you only use one of these events. 

`mouseover` fires when you touch an element, `mouseout` when you touch something else

No hover on touchscreen and no real way round it.

###Stick with Click
- `click` events work everywhere - not a mouse event.
- should have been called `activate`
- works with touches, keyboard, mouse


