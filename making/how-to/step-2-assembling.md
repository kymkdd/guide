---
description: (the easy part)
---

# step 2 : assembling

now that you got the frames its time to move on to the simpliest part of this guide, gifski

heres the command youre going to use everytime pretty much

```text
gifski --fps [fps] -o output.gif out*.png
```

once again lets go over the command

`gifski` like `ffmpeg` is just here to call the command

`--fps` like `-r` in ffmpeg is your framerate, no complexity here you just want that value to match the one you used in the previous command

`-o output.gif` defines where you want to output your gif and how you want to name it

`out*.png` is the input frames that you exported previously, i kept the naming scheme from the previous command but it can be changed obviously, `*` is a wildcard and will match anything after `out` in this case, gifski is pretty smart and will build the gif using frames in order based on the digits that ffmpeg appended to your output frames

{% hint style="warning" %}
#### on screens

you should note that gifski will stop assembling a gif if one of the frames has a different size than the others so you want to ensure that all of your frames use identical dimensions, if you exported them using ffmpeg in the previous step this shouldnt be an issue but if you ever make a gif manually you will need to double check
{% endhint %}



