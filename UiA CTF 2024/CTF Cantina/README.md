In this CTF challenge, from the Web category, we are provided with a website at: https://ctf-cantina.chall.uiactf.no

The website lets us see the available dishes from both the UK aswell as Norway. 

In the "About us" section, we can see that the company is currently located in Norway, the UK, the Netherlands, Germany and Belgium

Considering we are only shown Norwegian and British menu's in the homepage, i suspected that the flag is located in one of the other menus

I opened the homepage is burpsuite. The request headers were:

```
GET /api/content HTTP/2
Host: ctf-cantina.chall.uiactf.no
Sec-Ch-Ua: "Chromium";v="121", "Not A(Brand";v="99"
Accept: application/json, text/plain, */*
Accept-Language: nb-NO
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://ctf-cantina.chall.uiactf.no/
Accept-Encoding: gzip, deflate, br
Priority: u=1, i
```

I figured I could change the ```Accept-Language: nb-NO``` to ```de-DE``` or ```nl-NL``` to change the menu. I first tried Germany:

```Accept-Language: de-DE```

And i was immediately met with the flag in one of the dish panels in the menu:

```UiACTF{ju57_th3_G4b4gOO1}```
