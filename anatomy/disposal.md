---
description: >-
  (if you found this guide from my twitter this might be the part you were
  looking forward to)
---

# disposal

the spec defines the following methods of disposal

<table>
  <thead>
    <tr>
      <th style="text-align:center">value</th>
      <th style="text-align:center">name</th>
      <th style="text-align:left">meaning</th>
      <th style="text-align:center">gifsicle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:center">0</td>
      <td style="text-align:center">unspecified</td>
      <td style="text-align:left">no disposal specified
        <br />the decoder is not required
        <br />to take any action</td>
      <td style="text-align:center"><code>none</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:center">1</td>
      <td style="text-align:center">do not dispose</td>
      <td style="text-align:left">do not dispose
        <br />the graphic is to be left in place</td>
      <td style="text-align:center"><code>asis</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:center">2</td>
      <td style="text-align:center">restore to background</td>
      <td style="text-align:left">
        <p>restore to background color</p>
        <p>the area used by the graphic</p>
        <p>must be restored to the background color</p>
      </td>
      <td style="text-align:center"><code>bg</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:center">3</td>
      <td style="text-align:center">restore to previous</td>
      <td style="text-align:left">
        <p>restore to previous</p>
        <p>the decoder is required to restore</p>
        <p>the area overwritten by the graphic with</p>
        <p>what was there prior to rendering the graphic</p>
      </td>
      <td style="text-align:center"><code>previous</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:center">4 - 7</td>
      <td style="text-align:center">reserved</td>
      <td style="text-align:left">
        <p>to be defined</p>
        <p>reserved for future use (lol)</p>
      </td>
      <td style="text-align:center">N/A</td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
`bg` and `previous` are seldom used methods nowadays, their functions were mostly for old browsers and low bandwidth back when .gifs were more common
{% endhint %}

{% hint style="info" %}
values `4` through `7` are reserved values that were introduced in revision 89a of the spec \(the latest\) for future use however, gif being an abandonned format those values are simply useless and as far as i know will be treated like `none`
{% endhint %}

at first glance the two methods you will want to use are `none` and `asis` , while they might seem to achieve a similar result theres one major difference between the two

`none` will replace the entire screen with another frame **as long as both frames are non transparent**

this is a pretty important thing to take note of since you almost never want to use non transparent frames except for the very first frame of your sequence, the reason behind that is that unless you have an insanely drastic change in palette between 2 consecutive frames its MUCH more efficient to allocate all 255 colors to the pixels who changed between the two frames and use the extra bit of transparency to apply a "mask" over your previous frame allowing you to maximise the amount of colors displayed since when you use `asis` the previous frames palette wil NOT override your active frames palette essentially allowing you to go well past the 255-6 colors per frame limit and have frames with thousands of colors at once

in practice, for a gif who actually uses motion the average amount of colors that is attainable using `asis` masks is between [1000 and 3000 ](https://github.com/xinntao/BasicSR/wiki/How-to-make-high-quality-gif-with-full-%28true%29-color)but for static images you can essentially reach 24 bit

![a &quot;24-bit&quot; gif making full use of asis masks](../.gitbook/assets/24bit.gif)

{% hint style="info" %}
i wondered once if this concept could be taken even further to make 30-bit \(HDR\) gifs however this is mathematically impossible due to the spec limitation of 8 bit per pixel, even if every single pixel was broken down to 255 values we would still only be able to achieve "8 bit" per channel aka "24 bit"
{% endhint %}



