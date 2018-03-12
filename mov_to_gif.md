Source: https://gist.githubusercontent.com/dergachev/4627207/raw/0d79b10e8df5e8cb798f7e376e154f9851aec251/GIF-Screencast-OSX.md

To capture the video (filesize: 19MB), using the free "QuickTime Player" application:

* Open "Quicktime Player", 
* Go to File -> New Screen Recording
* Selected screen portion by dragging a rectangle, recorded 13 second video. 
* Go to File -> Export -> As Movie
  * Saved the video in **full quality** with the filename `in.mov` 

To convert in.mov into out.gif (filesize: 48KB), open Terminal to the folder with `in.mov` and run the following command:

    ffmpeg -i in.mov -s 600x400 -pix_fmt rgb24 -r 10 -f gif - | gifsicle --optimize=3 --delay=3 > out.gif

Notes on the arguments:

* `-r 10` tells ffmpeg to reduce the frame rate from 25 fps to 10
* `-s 600x400` tells ffmpeg the max-width and max-height
* `--delay=3` tells gifsicle to delay 30ms between each gif
* `--optimize=3` requests that gifsicle use the slowest/most file-size optimization 
