# Loop utility library
Loop.js is a simple library which can be used for looping. Possible application areas include game prototypes and animations. Loop provides a nice alternative to the `setInterval` with increased control. Looping time can be changed on the fly and the loop can be paused. Loop provides the actual `dt` of the previous cycle which can be used for dynamic timestep calculations to increase smoothness.
## How to install
```html
<script src="Loop.js"></script>
```
## Examples
Set up a loop.
```javascript
let loop = new Loo({
  dt: 20,
  ontick(dt) {
    console.log(dt);//time of previous cycle in ms
  }
});
```
### Starting and stopping
```javascript
loop.start();

setTimeout(loop.stop, 1000);//stop loop after 1s
setTimeout(loop.start, 2000);//start loop again after 2s
```
### Options
```javascript
let options = {
  animationFrame: true,//use requestAnimationFrame instead of setTimeout, dt and FPS properties are ignored if value is set true
  FPS: 60,//alternative to the dt property - provide frames per second (FPS)
  dt: 16,//alternative to the FPS - provide target time between two cycles
};

let loop = new Loop(options)
```
