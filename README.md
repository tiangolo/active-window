# active-window
> Get active window title in Node.js.

Compatible with Linux, Windows 7+, and OSX;

## Description

This module exports a `getActiveWindow()` function that takes as parameters:

* `callback`: a function to process the results, given as a parameter to that callback. The parameter will be a `window` object with:
  * `app`: the name of the app running, the process name (e.g. `chrome`).
  * `title`: the title of the active window (e.g. `Facebook`).

The `return` of the `getActiveWindow()` function is a Node.js [`ChildProcess`](https://nodejs.org/api/child_process.html#child_process_class_childprocess) object. So you can, for example, kill that child process with the `.kill()` method.

## Usage

```javascript
var monitor = require('active-window');

callback = function(window){
  try {
    console.log("App: " + window.app);
    console.log("Title: " + window.title);
  }catch(err) {
      console.log(err);
  }
}
/*Watch the active window
  @callback
  @number of requests; infinity = -1
  @interval between requests
*/
//monitor.getActiveWindow(callback,-1,1);

//Get the current active window
var monitorProcess = monitor.getActiveWindow(callback);

// After some time, or right before closing your app,
// you might want to kill the subprocess
monitorProcess.kill();

```

## Tested on
- Windows
 - Windows 10
 - Windows 7
- Linux
  - Raspbian [lxdm]
  - Debian 8 [cinnamon]
  - Ubuntu 16.04
- OSX
  - Yosemite 10.10.1

## TODO

- Test on more operating systems.
- Use native APIs.

## License

MIT
