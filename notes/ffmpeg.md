##Fix missing video length

Copy the video stream to a new video.

```
  └─[$] <> ffmpeg -i input.webm -c copy fixed.webm
```

##Remove initial part of video

```
└─[$] <> ffmpeg -ss 00:00:38 -i fixed.webm  -c copy fixed_extracted.webm
```
