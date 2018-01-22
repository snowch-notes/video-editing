#### Get movie clip information:

 - `ffprobe -i output.mp4 -print_format json -loglevel fatal -show_streams -count_frames`
    - r_frame_rate - (FPS)
    - nb_frames - (number of frames)
    - width
    - height

Field info: https://www.ffmpeg.org/doxygen/3.0/structAVStream.html

#### Blender first steps

- From top bar select `Video Editing`
- Left view set to `Properties`
- In VSE:
  - Click Add -> Movie
  - Set strip properties: Length (nb_frames)
- In Timeline (bottom view)
  - Set start: 1
  - Set end: nb_frames

#### Render

##### Settings

- Set Properties/Render
  - Display `New Window`
- Set Properies/Dimensions;
  - Resolution: X Y % (from ffprobe width, height, 100%)
  - Frame Range: Start, End (from ffprobe nb_frames)
  - Frame Rate: (from ffprobe r_frame_rate) 
- Set Properties/Output
  - Set output folder
  - File format `FFmpeg video`
- Set Properties/Encoding
  - Presets `h264 in MP4`

##### Test

- Top view, Render Menu -> Render Animation

#### Highlight box

- Press F12 to open the current frame into the Image editor
- Select Menu: Mask -> Save as Image
- Edit the saved image using Inkscape, add a rectangle without fill
- In Inkscape select menu: Export Bitmap
  - Export Area: Drawing
  - Click Export, replacing Orignal
- In Blender
  - Open VSE
  - In strip editor, select menu: Add -> Image and open the edited image
