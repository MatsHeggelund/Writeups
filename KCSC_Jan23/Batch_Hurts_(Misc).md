## 7SD (Misc)

In this CTF challenge we are simply provided a batch file. The challenge description tells us the file contains a valid batch script, and that they bet we can't find the flag

I began by downloading the batch file, and I opened it in an IDE to see what it is before running it. When opening the file (not running it), I was faced with this:

![image](https://user-images.githubusercontent.com/20840927/213546535-5832e21f-8a02-4fe7-939b-a7f5aa27c83e.png)


On line 1 we can see that it runs the "set" command followed by a whole lot of random numbers and % signs. These are environment variables. After a quick google search
of the set command, I learned that the it is used to set an environment variable (or variables) on your computer. 

I tried running the batch file to see what would happen if the file got to set all of those environment variables. At first glance, nothing notable happened after it ran.

I opened cmd and typed "set" to view all environment variables on my pc. Using a linux based termianl will work aswell. However, even after running the batch file, I found no out-of-place environment variables.

After a tip from one of the KCSC organisers, i found out the batch file actually can't set environment variables by itself. So, I tried doing it manually.

After copy-pasting the contents of the batch file into cmd, I once again tried viewing all environment variables using "set". I was then faced with a large amount of
random environment variables. Scrolling through the long list, I spotted one line that actually made sense

![image](https://user-images.githubusercontent.com/20840927/213548053-12e07d6b-840e-4a31-880f-d992d4796cb2.png)


It was the flag: KCSC{serious_brain_pain}
