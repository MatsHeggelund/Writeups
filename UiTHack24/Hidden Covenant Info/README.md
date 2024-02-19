*The covenant is slowly advancing to New Mombasa. We managed to catch a photo they sent in their communications channel, however we do not have their location. We believe the covenant is communicating with photos. Your mission Rookie, is to figure out what their location is; by finding the hidden information within the photo.*

This CTF challenge, in the misc category, included an image named Yanmee.jpg.

Based on the challenge description hinting towards "the hidden information within the photo", i ran some different steganography tools, until steghide worked

```
steghide --extract -sf Yanmee.jpg
```

Steghide usually requires a passphrase. Since I didnt have any, i just pressed enter to submit a blank one. This worked, and the extracted data was written to "newflag.txt"

Reading the contents of this textfile revealed the first half of the flag: **UiTHack24{Airview** in addition to a bunch of obvious whitespace.

After getting lost in cyberchef and analyzing the whitespace in a text editor, we eventually concluded that it was actually "whitespace language". 

Uploading newflag.txt to the whitespace language decoder found on dcode.fr resulted in the second half of the flag being retrieved: **_outpost}**

Meaning the combined flag was as follows:

UiTHack24{Airview_outpost}




