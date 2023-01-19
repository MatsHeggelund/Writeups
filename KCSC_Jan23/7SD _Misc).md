In this CTF challenge we are provided an image of a schematic, and we are provided with a .txt file containing a series of letters. 
![d3b16a4356acf77e5bfb09822443428e](https://user-images.githubusercontent.com/20840927/213541909-ca6b28f3-0a53-45fa-be08-a7d7595d9b48.png)

Here is the provided schematic.

The .txt file reads as follows:
acdfg abdefg adef aef abdefg abc d acdfg abdefg abcdfg d bcdeg bc acdfg abefg def abcefg bcdfg

We are tasked with finding out what kind of unit this is, and to find out a way to read the flag.

We can quickly identify this as a schematic of a 7 Segment Display by studying the schematic. This is also obvious due to the challenge name (7SD).
The .txt file consists of a series of words made up of letters between a and g. It seems to be some kind of code. 
My first guess was that the abcdefg letters could be code for which part of the 7SD will be lit up in each case. There are 7 different letters for each part of the 7SD.
I then looked up an online 7 Segment Display decoder. I used the one at https://www.dcode.fr/7-segment-display, but other can work just as fine.

After copy-pasting the contents of the .txt file into the decoder, we are faced with this result:
![image](https://user-images.githubusercontent.com/20840927/213544021-e593e59c-36d1-4e2b-86b3-835f58f15b99.png)

The flag may be difficult to interpret at first glance, but the challenge tells us the flag consists of lower-case letters seperated by an undersocre
The flag is therefore: KCSC{secret_seg_display}
