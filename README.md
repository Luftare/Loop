# Loop utility library
Loop.js is a simple library for loops with added functionality compared to the native `setInterval`. Example application areas include game prototypes and animations. Delta time between cycles (ie. frequency) can be changed on the fly and the loop can be paused and restarted again. Loop provides the actual `dt` of the previous cycle which can be used for dynamic timestep calculations.
## How to install
```html
<script src="Loop.js"></script>
```
## Examples
Set up a loop. Provide an options object where the `onTick` is the function to be called on each cycle.
```javascript
let loop = new Loop({
  dt: 20,
  onTick(dt) {
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
### Getters and setters
Get and set either the FPS or dealt time (dt) format while both change the frequency of the loop.
```javascript
loop.FPS = 1;//loops once per second --> dt is 1000ms
console.log(loop.FPS, loop.dt);//--> 1, 1000
loop.dt = 16;//sets the looping delta time to 16ms
console.log(loop.FPS, loop.dt);//--> 60, 16
console.log(loop.lastDt);//Actual time of the last cycle in ms. Since timeouts are inaccurate in JS in general, loop.lastDt is often 0...5ms away from the targeted time. Most of the time delayed.
```
Use the `running` property to check if the loop is running.
```javascript
console.log(loop.running);//false
loop.start();
console.log(loop.running);//true
```
