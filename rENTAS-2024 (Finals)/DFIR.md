# Hidden Zombie

First I checked the png using various stega tools online, but I was unable to upload it for some
reason? Since I can still view the image, I tried to check if it was corrupted using pngcheck. It
shows CRC was corrupted, meaning the File Header was manipulated.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/hiddenzombie1.png)

As previous CTF file headers questions often use image width and height manipulation, I tried to
change it here as well.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/hiddenzombie2.png)

I changed the height to match the width, 1024x1024 (00 00 04 00 00 00 04 00) instead of 1024x921 (00 00 04 00 00 00 03 99)

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/hiddenzombie3.png)

Then I viewed the image again, and there is the flag.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/hiddenzombie4.png)

Flag: ```RWSC{z0mb13_4tt4ck_1nc0m1ng}```
