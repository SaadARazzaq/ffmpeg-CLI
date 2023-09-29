# ffmpeg-CLI

## Pre-Requisites
To use FFMPEG, MEet the below Requirements by following these steps:

1. **Install FFmpeg** (if not already installed):
   
   If you haven't already, you can install FFmpeg by following the instructions for your specific operating system. Visit the [FFmpeg website](https://www.ffmpeg.org/download.html) for installation guides.

2. **Use the FFmpeg Command**:

   Open your terminal or command prompt in your directory where your (To Be Converted) file is placed and run desired command for conversion 🙂

---
## Video To GIF
---
```bash
ffmpeg -i input_video.mp4 -vf "fps=10,scale=320:-1:flags=lanczos,setpts=PTS/10" -c:v gif -t 10 output.gif
```
👉 `-i input_video.mp4` - Input video file (replace with your video file).

👉 `-vf "fps=10,scale=320:-1:flags=lanczos,setpts=PTS/10"` - Video filter options:

- fps=10 - Sets the frame rate of the GIF to 10 frames per second.
- scale=320:-1 - Resizes the video to a **width** of 320 pixels while maintaining the aspect ratio.
- flags=lanczos - Specifies the resampling algorithm for high-quality scaling.
- setpts=PTS/10 - Adjusts the presentation timestamps to control the video duration (in this example, fixing length it down to 10 seconds).

👉 `-c:v gif` - Specifies the codec for the output video as GIF.

👉 `-t 10` - Sets the duration of the output GIF to 10 seconds (you can change this value).

👉 `output.gif` - Output GIF file (you can choose the desired output file name).

**If you want to create a GIF of the entire video without fast-forwarding or cropping, you can use the following FFmpeg command:**
```bash
ffmpeg -i input.mp4 -vf "fps=24,scale=1600:-1:flags=lanczos" -c:v gif output.gif
```

---
## GIF To Video
---
```bash
ffmpeg -i input.gif -vf "fps=30,scale=1280:-1:flags=lanczos" -c:v libx264 -crf 20 -pix_fmt yuv420p output_video.mp4
```
👉 `-i input.gif` - Input GIF file (replace with your GIF file).

👉 `-vf "fps=30,scale=1280:-1:flags=lanczos"` - Video filter options:

- fps=30 - Sets the frame rate of the output video to 30 frames per second. You can adjust this value to control the video's frame rate.
- scale=1280:-1 - Resizes the video to a **width** of 1280 pixels while maintaining the aspect ratio. Modify the width as needed.
- flags=lanczos - Specifies the resampling algorithm for high-quality scaling.

👉 `-c:v libx264` - Specifies the video codec as libx264, a popular video codec.

👉 `-crf 20` - Constant Rate Factor (CRF) for video quality. Lower values (e.g., 18) result in higher quality but larger file sizes. Higher values (e.g., 30) reduce quality but yield smaller files. 20 is a good compromise for decent quality and reasonable file size.

👉 `-pix_fmt yuv420p` - Sets the pixel format to yuv420p, which is widely supported by video players.

👉 `output_video.mp4` - Output video file (you can choose the desired output file name).

