---
description: (this is gonna turn into a rant pretty quickly)
---

# delay

now heres the technical part most people probably care about, the animation part so heres a simple table showing delays from 1 to 10 and their corresponding framerate for reference

{% tabs %}
{% tab title="table" %}
| delay, in n/100th of a second | framerate, in frames/second |
| :--- | :--- |
| _1_ | _100.0_ |
| 2 | 50.0 |
| 3 | 33.3 |
| 4 | 25.0 |
| 5 | 20.0 |
| 6 | 16.7 |
| 7 | 14.3 |
| 8 | 12.5 |
| 9 | 11.1 |
| 10 | 10.0 |

framerates are rounded up to the first closest decimal place
{% endtab %}

{% tab title="graph" %}
![](../.gitbook/assets/save.png)
{% endtab %}
{% endtabs %}

now you may be wondering "ellie where is 60fps?" or "why is 1/100th italicised?" and uve just fallen into my trap

![](../.gitbook/assets/image.png)

see, as definied in the [spec](https://www.w3.org/Graphics/GIF/spec-gif89a.txt), gifs work in hundredths of a second, the smallest possible value being 1 which translates to displaying the frame for 1/100th of a second, while this value is in the spec, you generally dont want to use it as many browsers and software simply do not support it and will "correct" values specified as 1 to 2 or even 10 in some cases which is a very perceptible difference in timing and will completely throw off your animation thats why you generally dont want to use anything besides 2~10

  
ok, meme aside





