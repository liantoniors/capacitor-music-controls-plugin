# capacitor-music-controls-plugin
An update to Cordova Music Controls plugin to support Capacitor


[documentation in progress]

# installation

npm i capacitor-music-controls-plugin


Android (thanks @lbesiche)

After you install the plugin go to your MainActivity.java

import this path:
import com.ingageco.capacitormusiccontrols.CapacitorMusicControls;

add class inside bridge activity:
add(CapacitorMusicControls.class);

Finally, run:
npx cap sync android
