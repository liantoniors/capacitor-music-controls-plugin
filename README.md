# capacitor-music-controls-plugin
An update to Cordova Music Controls plugin to support Capacitor


[documentation in progress]

# work in progress

this integration is a work in progress. currently, ios is mostly working (some bugs), and android is unfinished.

PRs for rounding out the functionalities are encouraged.


# installation

npm i capacitor-music-controls-plugin


## Android (thanks @lbesiche)

After you install the plugin go to your MainActivity.java

import this path:
import com.ingageco.capacitormusiccontrols.CapacitorMusicControls;

add class inside bridge activity:
add(CapacitorMusicControls.class);

Finally, run:
npx cap sync android


# example usage in your app

usage of this plugin is very similar to cordova-music-controls plugin. here is an example of importing the plugin and using it within your app. 


At the top of your file import Plugins and this package

`import { Plugins } from '@capacitor/core'; import { CapacitorMusicControls } from 'capacitor-music-controls-plugin';`

Creating the controls:

`const { CapacitorMusicControls } = Plugins;`

Create your options - exact same as Cordova Music Controls

`var options = {}`

Create the controls

`CapacitorMusicControls.create(options);`

Update whether the music is playing true/false

`CapacitorMusicControls.updateIsPlaying({isPlaying: true}).catch(function(error){
  console.log("error reported:");
  console.log(error);
});`

Listen for events and pass them to your handler function

`CapacitorMusicControls.addListener('controlsNotification', (info: any) => {
    console.log('controlsNotification was fired');
    console.log(info);
    self.handleControlsEvent(info);
});`



Example event handler

`handleControlsEvent(action){

	console.log("hello from handleControlsEvent")
	const message = action.message;

	console.log("message: " + message)

	switch(message) {
		case 'music-controls-next':
			// next
			break;
		case 'music-controls-previous':
			// previous
			break;
		case 'music-controls-pause':

			// paused
			break;
		case 'music-controls-play':
			// resumed
			break;
		case 'music-controls-destroy':
			// controls were destroyed
			break;

		// External controls (iOS only)
		case 'music-controls-toggle-play-pause' :
			// do something

			break;
		case 'music-controls-seek-to':
			// catch seeking, example shown
                            const { CapacitorMusicControls } = Plugins;

			const seekToInSeconds = action.position;


			CapacitorMusicControls.updateElapsed({
				elapsed: this.playerPosition,
				isPlaying: true
			});
			// Do something
			break;
		case 'music-controls-skip-forward':
			// Do something
			break;
		case 'music-controls-skip-backward':
			// Do something
			break;

		// Headset events (Android only)
		// All media button events are listed below
		case 'music-controls-media-button' :
			// Do something
			break;
		case 'music-controls-headset-unplugged':
			// Do something
			break;
		case 'music-controls-headset-plugged':
			// Do something
			break;
		default:
			break;
	}
}`

