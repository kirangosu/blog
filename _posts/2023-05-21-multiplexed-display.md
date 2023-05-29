---
layout: post
tags: nerd electronics programming microcontroller raspberry pico ssd multiplexing
cat: post
date: 2023-05-21
description: How does a seven segment display work?
---

You must have noticed this in movies or any other recorded videos - if the recorded video displays seven segment displays they always flicker. Have you ever wondered why? The answer to that is multiplexed display. Would you like to know more, read ahead.

First some basics.
A seven segment display (SSD), as the name indicates it has 7 segments, like below. For our understanding, I've marked them with alphabets. Each segment is a diode. 

```text
                                   
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


```text

                       |\  |
            anode (+)  | \ | cathode (-)
            ___________|  \|__________
                       |  /|
                       | / |
                       |/  |

```


To make a LED ON, we connect the positive terminal of the power supply to the anode and the negative supply to the cathode - remember the reverse polarity wont make the LED ON. At the same time, the LED will *not* be damaged if we reverse the polarity, because we just learnt, on how a diode works.

A SSD will have 8 pins, 7 anodes, one for each diode and 1 common cathode.

So, if we have to make a `1`, then we connect the anodes of `b` and `c` to the positive supply and connect the only one common cathode to the negative.

```text

                     Circuit  


                            (a)
               _____/ ______|\|_______
              |             |/|       |
              |                       |
              |             (b)       |
              |_____--______|\|_______|
              |             |/|       |
              |                       |
              |             (c)       |                          Output
              |_____--______|\|_______|          
              |             |/|       |                             |    
              |                       |                             |  (b)
              |             (d)       |                              
     _________|_____/ ______|\|_______|_______                      |
    Vcc       |             |/|       |       |                     |  (c)
    (+)       |                       |     -----        
              |             (e)       |      ---  Gnd
              |_____/ ______|\|_______|       -   (-)
              |             |/|       |
              |                       |
              |             (f)       |
              |_____/ ______|\|_______|
              |             |/|       |
              |                       |
              |             (g)       |
              |_____/ ______|\|_______|
                            |/|
     

```                                  

Similarly, for a `2`, we connect the anodes of `a`, `b`, `g`, `e` and `d` to Vcc and then connect the cathode to Gnd.

```text

                     Circuit  

                            (a)
               _____--______|\|_______
              |             |/|       |
              |                       |
              |             (b)       |
              |_____--______|\|_______|
              |             |/|       |
              |                       |
              |             (c)       |                           Output
              |_____/ ______|\|_______|                            (a)
              |             |/|       |                           -----
              |                       |                                |
              |             (d)       |                            (g) | (b)
     _________|_____--______|\|_______|_______                    ----- 
    Vcc       |             |/|       |       |                  |
    (+)       |                       |     -----            (e) |
              |             (e)       |      ---  Gnd             -----
              |_____--______|\|_______|       -   (-)              (d)
              |             |/|       |
              |                       |
              |             (f)       |
              |_____/ ______|\|_______|
              |             |/|       |
              |                       |
              |             (g)       |
              |_____--______|\|_______|
                            |/|
     

```

And so on.


So, what is the problem, you ask? Well, there isn't any. Yes, there is no problem, when we deal with one seven segment display. But most often we see SSD's always grouped - we need at least 4 SSDs to display time, for example. 

Let us take a 2 SSDs together to explain the problem - it would be something like below:

```text
                  (a)                   (a)        
                 -----                 -----      
                |     |               |     |     
            (f) | (g) | (b)       (f) | (g) | (b) 
                 -----                 -----      
                |     |               |     |     
            (e) |     | (c)       (e) |     | (c) 
                 -----                 -----      
                  (d)                   (d)       
         
               digit -  1            digit - 2

```

In this case, the anodes of `a` of both the digits are interconnected. Similarly, every segment of each digit is interconnected to the corresponding segment of the other digit. But each digit has its own cathode. It would be something like below.

```text
                                                    (a)
               _____/ ______________________________|\|_______
              |         |                           |/|       |
              |         |                                     |
              |         |                           (b)       |
              |_____/ __c___________________________|\|_______|
              |         |   |                       |/|       |
              |         |   |                                 |
              |         |   |                       (c)       |
              |_____/ __c___c_______________________|\|_______|
              |         |   |   |                   |/|       |
              |         |   |   |                             |
              |         |   |   |                   (d)       |
     _________|_____/ __c___c___c___________________|\|_______|_______
    Vcc       |         |   |   |   |               |/|       |       |
    (+)       |         |   |   |   |                         |     -----
              |         |   |   |   |               (e)       |      ---  Gnd
              |_____/ __c___c___c___c_______________|\|_______|       -   (-)
              |         |   |   |   |   |           |/|       |
              |         |   |   |   |   |                     |
              |         |   |   |   |   |           (f)       |
              |_____/ __c___c___c___c___c___________|\|_______|
              |         |   |   |   |   |   |       |/|       |
              |         |   |   |   |   |   |                 |
              |         |   |   |   |   |   |       (g)       |
              |_____/ __c___c___c___c___c___c_______|\|_______|
                        |   |   |   |   |   |   |   |/|
                        |   |   |   |   |   |   |
                        |   |   |   |   |   |   |
                        |   |   |   |   |   |   |
                        |   |   |   |   |   |   |
                        |   |   |   |   |   |   |   (a)
                        |___c___c___c___c___c___c___|\|_______
                            |   |   |   |   |   |   |/|       |
                            |   |   |   |   |   |             |
                            |   |   |   |   |   |   (b)       |
                            |___c___c___c___c___c___|\|_______|
                                |   |   |   |   |   |/|       |
                                |   |   |   |   |             |
                                |   |   |   |   |   (c)       |
                                |___c___c___c___c___|\|_______|
                                    |   |   |   |   |/|       |
                                    |   |   |   |             |
                                    |   |   |   |   (d)       |
                                    |___c___c___c___|\|_______|_______
                                        |   |   |   |/|       |       |
                                        |   |   |             |     -----
                                        |   |   |   (e)       |      ---  Gnd
                                        |___c___c___|\|_______|       -   (-)
                                            |   |   |/|       |
                                            |   |             |
                                            |   |   (f)       |
                                            |___c___|\|_______|
                                                |   |/|       |
                                                |             |
                                                |   (g)       |
                                                |___|\|_______|
                                                    |/|
       



```

Ok, we are close to the problem now. Let us say, we want to display `21`, then we need to connect the anodes of `a`, `b`, `g`, `e` and `d` of the digit - 1 to positive and the anodes of `b` and `c` of digit - 2 to positive. However, the anodes corresponding segment of both the digits are interconnected. So the only possibility is to show `22` or `11`. In short, we will be able to show the same content in each digit. You get the problem? Yeah, that, precisely is the problem.

I'd recommend think of the potential solution. And if you find the solution, please do let me know.

I will publish the solution in my next post.

Thanks.