---
title: A little fun with the 12F675 and mikroC
author: silviu
type: post
date: 2009-09-17T18:19:19+00:00
url: /2009/09/17/a-little-fun-with-the-12f675-and-mikroc/
dsq_thread_id:
  - 48858489
categories:
  - old
tags:
  - temp_on

---
I have a small example that should get you going with the PIC 12F675 microcontroller and mikroC PRO. I am using the EasyPIC5 development board but I am sure you can adapt it to many development systems. It's just a small introduction you can use as a tutorial on getting started with a comon, cheap and simple microcontroller.

<!--more-->


```cpp
bit oldstate; // Old state flag

void main() {
ANSEL = 0; // Configure AN pins as digital
CMCON = 7; // Turn off the comparators
TRISIO = 0; // configure pins of GPIO as output
TRISIO3_bit = 1;
GPIO = 0xFF;
do {
if (Button(&GPIO, 3, 1, 1)) { // Detect logical one
oldstate = 1; // Update flag
}
if (oldstate && Button(&GPIO, 3, 1, 0)) {
// Detect one-to-zero transition
GPIO = ~GPIO; // Invert GPIO
oldstate = 0; // Update flag
} // beginning of a repeat loop
} while(1); // endless loop
}
```
Copy and paste the code above in MikroC PRO. You can use the free version as the PIC12F675 only has 1K flash memory. This small example changes the state of the LEDs on every press on the GPIO3 button (RA3 on the EasyPIC5). Don't forget to set MCLR and oscillator as **internal** - so you get three extra pins! GPIO3 is input only so we will use it for a button. Should you want to test this on a breadboard or something similar this should be the schematic:

<p style="text-align: center">
  <img decoding="async" loading="lazy" class="aligncenter size-full wp-image-486" title="schema_12f675_leds" alt="schema_12f675_leds" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/09/schema_12f675_leds.png" width="526" height="361" />
</p>

You can find it on [GitHub][1] .

 [1]: https://github.com/filviu/mikroc_bits