clock.js
========

* Clock counts time.
* Makes time useful.
* Clock uses setTimeout but is self correcting.
* Count down? Count up! Clock no care, but count down preferred.
* DOES NOT FIDDLE WITH THE DOM. Display time however you want.

Written with ♥ in [vanilla.js](http://vanilla-js.com/).

![vanilla button](http://vanilla-js.com/assets/button.png)

Usage
-----

```javascript
var display = document.getElementById('countdown');

var showTime = function (c) {
  // display time with leading zeros
  display.innerText = c.zeroPadded.hours + ':' +
    c.zeroPadded.minutes + ':' +
    c.zeroPadded.seconds;
}

var clock = new Clock({
    tick: function (clock) {
      // ticks happen 5 times per second.
    },
    second: function (clock) {
      showTime(clock);
    },
    finish: function (clock) {
      // SOUND THE ALARM!
      display.innerText = 'TIME IS UP!';
    }
});

// count down from 100 seconds
clock.start(0, 0, 100);

// clicking timer pauses countdown
display.addEventListener('click', function () {
  console.log('click!');
  if (clock.running) {
    clock.pause();
    display.innerText = 'PAUSED';
  } else {
    clock.unpause();
    showTime(clock);
  }
}, false);
```


