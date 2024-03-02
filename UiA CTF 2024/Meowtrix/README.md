This CTF challenge, from the Stego category, provides us with an image file named meowtrix.png

The image depicts a cat with a strange, flannel-like pattern in the background. 

After running all the common Stego tools with no results, we opted for more creative ideas.

This challenge invoved a lot of trial and error, but my teammate eventuallt tried running the image through an online bar-code scanner.

From the online bar-code scanner at ```https://online-barcode-reader.inliteresearch.com```, we got the following output:

```
Barcode:	1 of 1	Type:	Code128	
Length:	11	Rotation:	left	
Module:	16.8pix	Rectangle:	{X=692,Y=40,Width=372,Height=1260}

UIACTFRUTER
```
Converting it to the CTF's flag format: ```UIACTF{RUTER}```
