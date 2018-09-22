# ffmpeg/ffprobe

### video / audio info
```
ffprobe -i input.mp4
```
### grab mpg from dvd
```
# backup dvd to VOB, IFO, BUP
dvdbackup  -M -i /dev/sr0 -o ~/Videos/dvd-backup
# convert VOB to MPG  
ffmpeg -i VTS_01_1.VOB -c:v copy -c:a copy -f dvd VTS_01_1.MPG
```
See also - http://superuser.com/questions/1106767/vob-converted-to-mpg-with-ffmpeg-doesnt-include-the-audio

### Copy audio from video

Fast bitwise copy, does not alter (e.g. reduce quality) of audio

```
# copy audio from video using input codec
ffmepg -i input.mp4 -vn -c:a copy output.aac
```

### Slice off start or end of video

```
ffmpeg -ss 00:00:04 -i input.mov -c copy -t 00:02:52 cut.mov
```

### record desktop on os x
```
# list devices (https://trac.ffmpeg.org/wiki/Capture/Desktop#macOS)
ffmpeg -f avfoundation -list_devices true -i ""
ffmpeg -f avfoundation -i "<screen device index>:<audio device index>" output.mkv

# or with mouse clicks and cursor captured
ffmpeg -f avfoundation -capture_cursor 1 -capture_mouse_clicks 1 -i "<screen device index>:<audio device index>" output.mkv

# convert to mp4
ffmpeg -i output.mkv -codec copy output.mp4

# fps, num frames - (can take a while) - useful for setting up blender
ffprobe -i output.mp4 -print_format json -loglevel fatal -show_streams -count_frames
```

### Split movie into equal chunks

https://github.com/c0decracker/video-splitter

### See also

https://www.youtube.com/watch?v=BiMP_hN8f6s

- reduce audio bitrate (e.g. if it is too big to store/stream)
- copy clip (e.g. extract 2m clip starting at 13m 28s)
- video snapshots (e.g. quickly skim through a video)
