# Zombiefy

The task provided us with a kowai file without an extension. The file contains a cipher of <b>Base32</b> and when rendered produces a <b>JPG</b>

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/kowai.png)

Looking at the image we can see an ICC Profile, the hint linked us to ```jdvrif```, which encrypts and embeds data within multiple 65KB ICC_Profile blocks of the JPG image.

Extracting the data within the image we receive previously, we receive a <b>MP3</b> file.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/kowai2.png)

With the hint, it leads us to ```AudioStego```. Using it to extract the string inside the mp3 results in hex code.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/kowai3.png)

insert the given hex values into cyberchef to retrieve the flag

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/kowai4.PNG)

Flag: ```RWSC{kur0n3kO}```
