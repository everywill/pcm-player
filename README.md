# pcm-player
A refined pcm player for web, automatically handles AudioContext-resume to be able to play sound, and provides friendly API for users.

# How to use
```
const player = new FUPCMPlayer({
    encoding: '16bitInt',  // 8bitInt16bitInt 32bitInt 32bitFloat
    channels: 1,           
    sampleRate: 16000,     
});

player.feed(pcmData)  // pcmData is a typedArray carrying pcm data with specified encoding

player.destroy();     // recycle anthing allocated by the player
```
After data is fed into the player, it will be scheduled to be played automatically. On the air you can continuously feed pcm stream in.

# Other API
```
player.setRequestStop(); // stop playing after current pcm-segmengt is consumed

player.setOnEnd(callback);  // callback will be triggered when stop-request is fulfilled

player.interrupt();      // stop playing immediatedly

player.getTimestamp();   // get elapsed time against first bit played, especially useful when the player is used as a audio-clock

player.volume(someVolume)
```
