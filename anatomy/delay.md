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
| 100 | 1.0 |

framerates are rounded up to the first closest decimal place
{% endtab %}

{% tab title="graph" %}
![](../.gitbook/assets/save.png)
{% endtab %}
{% endtabs %}

now you may be wondering "ellie where is 60fps?" or "why is 1/100th italicised?" and uve just fallen into my trap

![](../.gitbook/assets/image.png)

see, as definied in the [spec](https://www.w3.org/Graphics/GIF/spec-gif89a.txt), gifs work in hundredths of a second, the smallest possible value \(integers only\) being 1 which translates to displaying the frame for 1/100th of a second, while this value is in the spec, you generally dont want to use it as many browsers and software simply do not support it and will "correct" values specified as 1 to 2 or even 10 in some cases which is a very perceptible difference in timing and will completely throw off your animation thats why you really dont want to use anything besides 2~10

ok, meme aside the reason why 60 fps are not really a thing in practice is due to the fact that 100 cannot be divided by an integer to something that equate 60, in that case i would just tell people to use 2/100th which equates to 50fps and is usually plenty enough however for the purpose of this guide we are going to assume you are really stubborn and really want to make a 60fps gif

well, bad news, thats still not doable mathematically speaking because of the aforementioned reasons but this gives me an opportunity to highlight the used of mixed delays

the cool thing about gifs is that much like colors as explained in the previous page, each frame in a gif is either relying on a global plaette or on its own palette and this also applies to delays, each frame can either be dependent on a globally set delay or have its own delay which lets us get a lot more creative with our framerate, using that feature one can easily make animations with minimal size by setting a higher delay on a specific frame to hold it in place instead of duplicating it multiple times, however this guide is more centered around going from video to gif so i wont go in details about that

the way mixed delays work as the name indicate is by interlacing together 2 \(or more but usually just 2\) different delays to attain a "percieved" \(and numerical\) framerate that is as close as possible to the target framerate, usually the process consist on finding what i call a "key" delay which is the one you want to use for most of the frames and a "compensation" delay which is a delay you want to use punctually at a constant rate across the gif to reach the desired framrate over a set amount of frames

what i just explained might seem complicated but it actually isnt so lets go back to our 60 fps and try to craft it using what i just explained







