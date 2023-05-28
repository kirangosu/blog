---
layout: post
tags: nerd electronics programming microcontroller raspberry pico ssd "seven segment display" multiplexing
cat: post
date: 2023-05-21
description: How does a seven segment display work?
---

You must have noticed this in movies or any other recorded videos - if the recorded video displays seven segment displays they always flicker. Have you ever wondered why? The answer to that is multiplexed display. Would you like to know more, read ahead.

First some basics.
A seven segment display (SSD), as the name indicates it has 7 segments, like below. For our understanding, I've marked them with alphabets. Each segment is a diode. 

```
                                   
                     (a)
                    -----
                   |     |
               (f) | (g) | (b)
                    -----
                   |     |
               (e) |     | (c)
                    -----
                     (d)
```

Now, you might ask, what is the problem. To understand the problem, lets learn a tad bit of a diode.

A diode, as we know, passes current in one direction - and this is the feature that we find most useful in most of the circuits and we see today. A diode is symbolized as below.


```

                       |\  |
            anode (+)  | \ | cathode (-)
            ___________|  \|__________
                       |  /|
                       | / |
                       |/  |

```


To make a LED ON, we connect the positive terminal of the power supply to the anode and the negative supply to the cathode - remember the reverse polarity wont make the LED ON. At the same time, the LED will *not* be damaged if we reverse the polarity, because we just learnt, on how a diode works.

A SSD will have 8 pins, 7 anodes, one for each diode and 1 common cathode.

So, if we have to make a 1, then we connect the anodes of `b` and `c` to the positive supply and connect the only one common cathode to the negative.

```
                          (a)
               _____/ __________|\|_______
              |                 |/|       |
              |                           |
              |           (b)             |
              |_____--__________|\|_______|
              |                 |/|       |
              |                           |
              |           (c)             |
              |_____--__________|\|_______|
              |                 |/|       |
              |                           |
              |           (d)             |
     _________|_____/ __________|\|_______|_______
    Vcc       |                 |/|       |       |
    (+)       |                           |     -----
              |           (e)             |      ---  Gnd
              |_____/ __________|\|_______|       -   (-)
              |                 |/|       |
              |                           |
              |           (f)             |
              |_____/ __________|\|_______|
              |                 |/|       |
              |                           |
              |           (g)             |
              |_____/ __________|\|_______|
                                |/|
     

```

The output would be something like below:
```
                                             
                         |
                         | (b)
                         
                         |
                         | (c)
                         
```                                             

Similarly, for a 2, we connect the anodes of `a`, `b`, `g`, `e` and `d` to Vcc and then connect the cathode to Gnd.

```
                          (a)
               _____--__________|\|_______
              |                 |/|       |
              |                           |
              |           (b)             |
              |_____--__________|\|_______|
              |                 |/|       |
              |                           |
              |           (c)             |
              |_____/ __________|\|_______|
              |                 |/|       |
              |                           |
              |           (d)             |
     _________|_____--__________|\|_______|_______
    Vcc       |                 |/|       |       |
    (+)       |                           |     -----
              |           (e)             |      ---  Gnd
              |_____--__________|\|_______|       -   (-)
              |                 |/|       |
              |                           |
              |           (f)             |
              |_____/ __________|\|_______|
              |                 |/|       |
              |                           |
              |           (g)             |
              |_____--__________|\|_______|
                                |/|
     

```

The output would be like this.

```

                      (a)
                     -----
                          |
                      (g) | (b)
                     -----
                    |
                (e) |
                     -----
                      (d)
```                                         

And so on.


So, what is the problem, you ask? Well, there isn't any. Yes, there is no problem, when we deal with one seven segment display. But most often we see SSD's always grouped - we need at least 4 SSDs to display time, for example. 

Let us take a 2 SSDs together to explain the problem - it would be something like below:

```
                  (a)              (a)        
                 -----            -----      
                |     |          |     |     
            (f) | (g) | (b)  (f) | (g) | (b) 
                 -----            -----      
                |     |          |     |     
            (e) |     | (c)  (e) |     | (c) 
                 -----            -----      
                  (d)              (d)       
```

To be continued...