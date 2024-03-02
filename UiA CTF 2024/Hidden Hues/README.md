This CTF challenge, from the Web category, provides us with a colorful website at https://hidden-hues.chall.uiactf.no/

Based on the challenge name, I immediately suspect the flag is connected to the colors used in the css file for the website

I open the sources for the website, and i find the css styles in the html file:

```
:root {
  --body-linear-color-1: #556941;
  --h1-linear-color-1: #435446;
  --multi-color-1: #7b4330;
  --multi-color-2: #313072;
  --h1-text-shadow-color-1: #355f34;
  --h1-linear-color-2: #52335f;
  --a-color-1: #435231;
  --marquee-lineaer-color-2: #4e3633;
  --marquee-lineaer-color-1: #5f5f7d;
}
```

I immediately think of concatenating these hex-values together and then decoding them in cyberchef. This is because I have done a similair solution in a previous CTF challenge.

The combined hex-string is: ```5569414354467b4330313072355f3452335f4352314e36335f5f7d``` 

Decoding this from hex in cyberchef, we are provided with the flag: ```UiACTF{C010r5_4R3_CR1N63__}```
