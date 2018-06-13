# Musical Shower Caddy
*Built by Brian Margolis (BrianMargolis2019 [at] u [dot] northwestern [dot] edu) in Professor Bryan Pardo's Digital Luthier course at Northwestern University.*

## What is the Musical Shower Caddy?
The Musical Shower Caddy is an ensemble of instruments built from soap bottles, toothbrushes, and other items one would find in a shower caddy. By using the included looper pedal-like functionality, a user can use the entire ensemble of instruments to create a layered performance.
![Musical Shower Caddy](/images/logo.png)

## Why would you ever build something like this? And who would use it?
I was motivated by the idea of taking something mundane and routine and injecting creativity into it through music. 

You'll need at least some musical skill to play the Musical Shower Caddy, including ability to play rhythms precisely and basic piano skills. Through experience, I've found that the most challenging aspect of performing on the Musical Shower Caddy is actually the swapping that occurs between instruments.

## What are the constituent components of the Musical Shower Caddy?
#### Digital
There are four digital components that either emit MIDI data or work to filter the audio as the last step in the signal chain.
1. Squeeze whistle - a soap bottle that emits a pitch that varies as it is squeezed
2. Looper pump - a pump bottle that works like a looper pedal
3. Toothbrush filter - a toothbrush that applies a lowpass filter to the entire audio stream based on how fast it's being accelerated
4. Slap bottle - a soap bottle that acts like a drum pad when smacked on the bottom

#### Acoustic
1. Squeeze melodica - a squeeze bottle hooked up to a [melodica](https://en.wikipedia.org/wiki/Melodica)
2. Shaker bottle - a bottle with a shaker egg hidden inside it

## Tech Stack
#### Digital Flow
All the digital components have sensors on them that are controlled by [Arduino](https://www.arduino.cc/) code. That Arduino code interprets the sensor output and packages it into a serial stream, which [Max](https://cycling74.com/products/max) reads in. From this information, Max creates MIDI data and sends it over to [Ableton](https://www.ableton.com/en/) - although any DAW could work in its place. Finally, Ableton sends the audio stream back over to Max, where some final filtering is done and playback occurs.

#### Acoustic Flow
All the acoustic instruments are mic'd and recorded straight into Ableton. Like the rest of the audio, it's sent back to Max before playback occurs.

## Lessons learned and future work
#### Lessons Learned
* Sensor data is **messy**, and that messiness propagates through the instrument and makes even a technically sound performance liable to contain error. A good example of what I mean can be found in the slap bottle - essentially, it's a MIDI drumpad. However, the difference in engineering between a commercial MIDI drumpad, built on a real budget by real hardware people over the course of months, and this approximation, created by having a CS major slap Arduino sensors together over the course of a few weeks is large. These reliability and consistency deficiencies are a major obstacle to this being used as a performance instrument; you just can't perform on an instrument you can't trust.
* It would've probably been better if I had started with a smaller scope - building 4 novel electronic instruments was a bigger challenge than I anticipated, even despite the relatively simplicity of each instrument. Each instruments being simple did make it easier to conceptualize and design, but having a lot of parts is a liability regardless of their simplicity. There was just so much that could've gone wrong: each of the four instruments could have failed (one did), the looper pedal could've gone haywire (it did), Max could have failed, the Arduino could've failed, Ableton could've failed, my computer could have nearly overheated and crashed (it did), I could've gotten really bad feedback when micing the acoustic instruments (I did), or I could have forgotten parts and had to sprint home and back right before the performance (I did, twice). Or a number of other unanticipated issues could have cropped up. Starting smaller and locking that part down till it's totally reliable, consistent, and battle-tested would have been a better approach than going as wide as I did.

#### Future Work
* A lot of the difficulty in performing with the Musical Shower Caddy comes from the issues with instrument reliability and precision. Better hardware, more time, and more capable software is the pathway to that.
* While the idea of making the Musical Shower Caddy an orchestra, played by multiple people, would make it much easier to play - switching between the instruments while operating the looper pedal can be tough - most people shower alone. So, it really needs to remain a solo performance, at least on its face. However, this doesn't preclude us from including a second performer controlling the DAW (Ableton, currently) hidden away. It already needs to be pretty strictly choreographed and structured, so you don't lose much in terms of improvisation. This would open up the door for timbral variation (everything's MIDI, so you can just hotswap instruments) as well as some live mixing/filtering that could be really interesting.
* The signal chain is somewhat convoluted at the moment (Arduino -> Max -> Ableton -> Max -> speakers) because of the feedback into Max. It would be good to find a way to do the last bit we do in Max in Ableton to simplify that - or better yet, using Max For Live, port the whole thing into Max. However, that option does force us to give up the interchangeability of our DAW choice.
* The visual aspect of this performance shouldn't be ignored - it's meant to look like showering as much as possible. Waterproofing the instruments and being able to do this with real water would be fantastic.