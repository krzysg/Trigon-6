# Trigon-6 FAQ



## Important Links

#### Users Forum
[Sequential Trigon-6 FORUM](https://forum.sequential.com/index.php/board,50.0.html)

#### Manuals
[Operation Manual v. 1.2, (english) Aug 2023](https://sequential.com/wp-content/uploads/2023/07/Trigon-6-Operation-Manual-1.2.pdf)  
[Operation Manual v. 1.1, (english) Nov 2022](https://sequential.com/wp-content/uploads/2022/12/Trigon-6-Users-Guide-1.1.pdf)  
[Benutzerhandbuch v. 1.2, (german) Dezember 2024](https://sequential.com/wp-content/uploads/2024/12/Trigon-6-Benutzerhandbuch.pdf)  
[MIDI Implementation v. 1.1](https://sequential.com/wp-content/uploads/2022/12/Trigon-6-MIDI-Implementation-1.1.pdf)  

#### Web links on Sequential website
[Trigon-6 NEW](https://sequential.com/modern-analog/trigon-6/)  
[Trigon-6 OLD (but useful as long as it works)](https://sequential.com/product/trigon-6/)  
[Trigon-6 UPDATE OS info](https://sequential.com/updating-the-Trigon-6-os/)  
[Trigon-6 SUPPORT](https://sequential.com/support/)  


## Troubleshooting hints from Sequential:

[General TIPS/HINTS](https://support.sequential.com/hc/en-gb/articles/9113506579474-Trigon-6-Keyboard-Troubleshooting)  
[A Brief Explanation on Calibration](https://support.sequential.com/hc/en-gb/articles/13687984487186-A-Brief-Explanation-on-Calibration)  


## Other
### Key combinations

#### Basic Preset
Basic preset is useful for creating a new sound from scratch:

1. Hold down the preset button.
2. Press the write button.

### SysEx format:

#### 1. Unpacking Trigon's pitch data from its SysEx dumps.
[source](https://forum.sequential.com/index.php?topic=7017.0)

Sequential use a well-documented technique to pack 8-bit values into 7-bit data in their dumps.  This is fine for parameter values up to 255.  The two Osc pitch parameters, however, need to store values up to 1400 which needs 11 bits and won't fit in the standard structure.  I tried Sequential support but got no help with this, being pointed at Soundtower, as apparently if this works then all must be ok.
I made a number of dumps with different saved values and was able to figure out that the missing 3 bits per Osc are stored in bytes 50 and 51, so these need unpacking along with the LSB 7 bits and relevant bit from the MSB byte.  Easy to do once you know where to look.  Hope this helps anyone else who gets stuck on this.  I suggested to Sequential they update their documentation to include these hidden bytes.


#### 2. Sysex Instrument ID for Trigon? 
[source](https://forum.sequential.com/index.php/topic,6792.0.html)

ID of Trigon is 0x39

However in Manual Version 1.1 and all later versions of manual - English 1.2 from August, 2023 but also in German version from December, 2024 there is still:

```
0010 1101 - Trigon-6 ID
or
0010 1101 - Geräte-ID
```

In MIDI Implementation Chart 1.1 it seems to be almost corrected but there is strange 'b' in a number:

```
0b11 1001 - Trigon-6 ID
```
