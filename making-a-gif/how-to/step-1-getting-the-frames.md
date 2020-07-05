---
description: (command line scary)
---

# step 1 : getting the frames

this step is the "hardest" part but its still very simple, for this you will need ffmpeg, all you need to do is

```bash
ffmpeg -i [file] (-vsync vfr) -r [fps] out%04d.png
```

  lets break down the command step by step

`ffmpeg` is just to call the command

`-i [file]` is your input, replace the bracketed part with the path to your file which can be any of the formats that ffmpeg supports including apng which can be useful for converting things like line stickers

`-r [fps]` is your framerate, to figure it out you can right click your file and check its properties however some formats like vp9/webm \(the one comonly used by youtube\) and apng \(line stickers\) will often not report their framerate correctly or worst case scenario, not at all, note that its preferable to use an integer for the framerate due to the delay shenanigans explained [previously](../../anatomy/delay.md)  
to fix that issue you might want to use `ffprobe` to obtain that info since its included with ffmpeg, a simple `ffprobe -i [file]` will suffice

`out%04d` is the output file the `out` part can be replaced by anything you want, `%04d` means that we will incrementally append 4 digits incrementally \(0000\) to whatever is before the `%`, if you want to add more padding digits or less you can change the 4 to any other number 

`.png` is rather obvious but the frames you output have to be in .png format exclusively so dont touch that bit

`-vsync vfr` is optional thats why i put it in parentheses, its only useful if your input source has a variable framerate, the issue with `-r` is that will enforce a consistent framerate when outputting frames regardless if the source has a constant or variable framerate, most videos have a consistent framerate but it honestly doesnt hurt to add this extra bit as it adds no penalty to the performance of the command and will make sure that frames are output properly even if your video is funky

