# step 1 : getting the frames

this step is the "hardest" part but its still very simple, for this you will need ffmpeg, all you need to do is

```bash
ffmpeg -i [file] (-vsync vfr) -r [fps] out%04d.png
```

  lets break down the command step by step

`ffmpeg` is just to call the command

`-i [file]` is your input, replace the bracketed part with the path to your file which can be any of the formats that ffmpeg supports including apng which can be useful for converting things like line stickers

`-r [fps]` is your framerate, to figure it out you can right click your file and check its properties however some formats like vp9/webm \(the one comonly used by youtube\) and apng \(line stickers\) will often not report their framerate correctly or worst case scenario, not at all  
to fix that issue you might want to use `ffprobe` to obtain that info

