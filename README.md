# Audio Toolkit JS
Version 1.3.1

## About
Audio Toolkit JS is a simple project i made to easily reproduce audio in my other projects. However, anybody that may want to use it is allowed to do so.

## Features
- Supports audio track list
- Randomizer
- Loops: all tracks or current track only
- Add tracks during the execution of the Audio Toolkit Player
- Volume options
- Real time audio track info
- Set or get current track via scripting
- Set or get playing audio's current time

## Setup
Clone this repository in the directory of your will.

    git clone https://github.com/augustofrade/audiotoolkitjs.git

Link the toolkit file to yours

    <script src="AudioToolkitJS/audiotoolkit.js"></script>
  
  And finally initialize it on your script file:
```
const audio = new AudioKit(songs,options);
audio.init();
```
**Important:** it's required to use `audio.init()`, otherwise your audio player won't work as it should.
See the text under "Initialization" to know more about "songs" and "options" arguments.

## Usage

### Initialization

 - **songs [array]:** the track list to be reproduced by the audio player.
 - **options[object] (optional):** options for the audio player that may be changed later.
	- **randomize[bool]:** whether the tracks will be reproduced in random order or not.
	- **loop["self", "all", undefined]:** whether the tracks will be looped when ending.
		- "self": loops the current audio track only.
		- "all": loops the track list after it has been finished.
		 - undefined / no parameter: after ending the track list won't be looped.
	- **onload[callback]**: Sets a callback function to be called when the audio's metadata has been loaded.
	- **volume[float]:** (0-1). Sets the volume of the audio player.

### Basic commands

- **.play()** : plays the current audio in the current time or from the start it if called again.
- **.pause()**: pauses the current playing audio.
 - **.next()** : reproduces the next audio in the track list order.
- **.previous()** : reproduced the previous audio in the track list order.
- **.addTracks(array)** : adds the tracks from the argument array to the track audio player list. 

### Track list info commands
- .tracks (get): returns the track list.
- .currentTrack (get/set): returns or sets the current track. Ex when setting it:
	- `.currentTrack = ...`
	- If not found on track list, an error will be thrown.
- .currentTime (get): returns the current time of the audio's reproduction in seconds.
- .duration (get): returns the current audio duration.
- .loop (get): returns the audio reproduction loop's type. See the available type under "Initialization".


### Audio Player commands

- .setLoop(): "self", "all" or undefined/nothing. Passing no arguments removes loop configuration.
- .randomize [bool] (get/set) : returns or sets whether a random audio will be selected when changing tracks.
- .muted [bool] (get/set) : returns or sets whether the player is muted or not.
- .volume[float] (get/set): (0-1). Sets the volume of the audio player.
- .trackInfo (get): returns the current audio info as an object, such as name of the file, duration and currentTime.
