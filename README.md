# Musical Shower Caddy
*Built by Brian Margolis (BrianMargolis2019 [at] u [dot] northwestern [dot] edu) in Professor Bryan Pardo's Digital Luthier Course at Northwestern University.*

## What is the Musical Shower Caddy?
The Musical Shower Caddy is an ensemble of instruments built from soap bottles, toothbrushes, and other items one would find in a shower caddy. By using the included looper pedal-like functionality, a user can use the entire ensemble of instruments to create a layered performance.

## Why would you ever build something like this? And who would use it?
I was motivated by the idea of taking something mundane and routine and injecting creativity into it through music. 

You'll need at least some musical skill to play the Musical Shower Caddy, including ability to play rhythms precisely and basic piano skills. Through experience, I've found that the most challenging aspect of performing on the Musical Shower Caddy is actually the swapping that occurs between instruments.

## What are the constituent components of the Musical Shower Caddy?
There are four digital components that either emit MIDI data or work to filter the audio as the last step in the signal chain.
1. Squeeze whistle - a soap bottle that emits a pitch that varies as it is squeezed
2. Looper pump - a pump bottle that works like a looper pedal
3. Toothbrush filter - a toothbrush that applies a lowpass filter to the entire audio stream based on how fast it's being accelerated
4. Slap bottle - a soap bottle that acts like a drum pad when smacked on the bottom

There are also two acoustic components that are mic'd up for performance.
1. Squeeze melodica - a squeeze bottle hooked up to a [melodica](https://en.wikipedia.org/wiki/Melodica)
2. Shaker bottle - a bottle with a shaker egg hidden inside it

## Tech Stack
All the various (digital) components have sensors on them that are controlled by [Arduino](https://www.arduino.cc/) code. That Arduino code interprets the sensor output and packages it into a serial stream, which [Max](https://cycling74.com/products/max) reads in. From this information, Max creates MIDI data and sends it over to [Ableton](https://www.ableton.com/en/) - although any DAW could work in its place. Finally, Ableton sends the audio stream back over to Max, where some final filtering is done and playback occurs.

## Lessons learned and future work
