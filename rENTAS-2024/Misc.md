# Hidden Discord

The task provides us with a discord link. Inside the discord was the given message.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/discord1.png)

the first part is found in the voice channel chat

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/discord2.PNG)

the second part is hidden from public view. So we require a special tool called ```ShowHiddenChannels```. This plugin requires the usage of ```BetterDiscord``` so make sure to install that as well.
With ShowHiddenChannels installed, we can now see the hidden channels and retrieve part 2 and part 4

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/discord3.PNG)

part 3 was the easiest one yet, located in plain sight inside the event description

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/discord4.PNG)

for part 5, the hint given was the server icon. So we try to retrieve the image. However, the source image was 64 pixel, making it unreadable to the human eye.
To enlarge it, we manipulate the ```size``` parameter used by discord until we can read part 5
![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/discord5.PNG)

Flag: ```RWSC{r34d_d15c0rd_d3v3l0p3r_API_r3f3r3nc3}```
