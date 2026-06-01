# Tap Tempo — Next Steps

## Better BPM Averaging

Swap the current two-tap interval calculation for a first-to-last formula using the full `tapTimes` array:

```js
BPM = Math.round((tapTimes.length - 1) / ((tapTimes[tapTimes.length - 1] - tapTimes[0]) / 60000));
```

No changes to the array needed — just replace the `60000 / intervalBetweenTaps` line with this.

## Reset Timeout

If no tap for 2 seconds, clear the array so the next tap starts fresh:

```js
clearTimeout(resetTimer);
resetTimer = setTimeout(() => { tapTimes = []; }, 2000);
```

Add this inside the click listener after `tapTimes.push(Date.now())`. Declare `let resetTimer;` up top with the other variables.
