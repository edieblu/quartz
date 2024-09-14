---
tags:
  - ✅
published: true
sr-due: 2027-02-03
sr-interval: 946
sr-ease: 250
---

⬅️ [[Execute Program JavaScript Concurrency]]
## Event loops
Custom event loop:
```js
/* Each event in the events array is an object {fn, runAt}.
 *   fn: the function to call.
 *   runAt: the timestamp when we should call the function. */
const events = [];

function runLoop() {
  while (events.length > 0) {
    const now = new Date().getTime();
    
    // Find the next event and run it if it's ready.
    for (let i=0; i<events.length; i++) {
      const event = events[i];
      if (now >= event.runAt) {
        events.splice(i, 1); // Remove the event at index i.
        event.fn();
        /* We changed the array that we're looping over, so abort the
         * loop. The outer loop will restart it anyway. */
        break;
      }
    }
  }
}

function queueEvent(fn, ms) {
  const now = new Date().getTime();
  const runAt = now + ms;
  events.push({fn, runAt});
}
```

- "Event loop" refers to the code that actually processes events, calling their callbacks. An "event queue" is the list of events that are waiting to run, like the `events` array in our examples here. You may see event loops called "message loops" or "message pumps", but these mean roughly the same thing.