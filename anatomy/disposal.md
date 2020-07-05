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
      <td style="text-align:center">4-7</td>
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

