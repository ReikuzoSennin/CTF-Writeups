# Mobile

We were given a long pdf of a forensice examination report for Lenovo P70. The task was to find the password for the phone. I was stumped at first, however with the hint given it became much more clearer.
The hint gave us a video of a hacker getting the password of someone's phone that contains bitcoin.


He uses gesture.key located in android/system. However this Lenovo P70 has a different system, where the gesture was located in data/system instead.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/dfir2.PNG)

Finding data/system in the pdf file resulted in an image file with SHA1. 

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/dfir1.PNG)

The password was encrypted into SHA1, so we need to decrypt it. Using an AndroidGestureCrack we were able to decrypt it.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/dfir3.PNG)

Flag: ```RWSC{875463120}```
