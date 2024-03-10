# Anti-Brute

Given the name, I tried to bruteforce it using burpsuite and the password list. The username
used was admin as per the task.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/antibrute1.png)

Obviously it did not work, but I decided to try again, however this time I removed the cookie
```PHPSESSID``` inside the header parameters. This makes every password use a different
session id, tricking the server into thinking it was from different sessions trying the password for
the first time, instead of the same session brute forcing multiple passwords.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/antibrute2.png) (No more session id in the payload position)


With a different session id in every password attempt, I got the flag.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/antibrute3.png)

Flag: ```RWSC{n0_brut3f0rc3_pl34s3}```


# BlackHole

I used the same web crawler from the preliminary rounds and adjusted it a bit. Instead of finding
```No directory found```. I tried finding ```flag.txt```, however there were too many instances. So back to
the drawing board.

```python
import requests
from bs4 import BeautifulSoup
from urllib.parse import urljoin, unquote
import webbrowser

visited_links = set()

def get_links(url):
  try:
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')
    links = soup.find_all('a', href=True)
    # Filter links whose text ends with '/'
    filtered_links = [urljoin(url, link['href']) for link in links if link.get_text().endswith('/')]
    return filtered_links
  except requests.exceptions.RequestException as e:
    print(f"Error retrieving links from {url}: {e}")
    return []

def visit_links_recursive(url):
  if url in visited_links:
    return
  print(f"Visiting: {unquote(url)}")
  try:
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')
    if "flag.txt" in response.text:
      print(f"flag.txt found at {url}")
    visited_links.add(url)
    links = get_links(url)
    for link in links:
      visit_links_recursive(link)
  except requests.exceptions.RequestException as e:
    print(f"Error visiting {url}: {e}")

def main():
  starting_url = 'https://blackhole.ctf.rawsec.com/'
  visit_links_recursive(starting_url)

if __name__ == "__main__":
  main()
```

I tried to read the challenge again carefully. I noticed some words are bolded. Namely ```very,
very, very deep hole```, ```BlackHole```, and ```very deep```. This did not mean anything at first glance.
However when I was scrolling through the discovered directories, I found that some directories
go deeper and deeper. This made my tiny brain go to work as I realized I should check the
deepest directory. However I was quickly let down as the flag.txt did not contain any flag. Talk
about clickbait!

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/blackhole1.png)

Reading the flag.txt, it said check back the url, so I was staring at the url for who knows how
long. Until my monkey brain clicked again as I realized the url looked like hex. I went to
cyberchef and there it is.

![image](https://github.com/ReikuzoSennin/CTF-Writeups/blob/main/assets/blackhole2.png)

Flag: ```RWSC{bl4ckh0le_iz_w0rmh0l3}```
