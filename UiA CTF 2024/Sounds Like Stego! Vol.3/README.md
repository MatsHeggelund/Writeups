In this CTF challenge, from the Stego category, we were provided with a .wav file. This is part 3 of a 3-part series regarding this .wav file.

When listening to the audio file, we can hear faint talking in the background. It sounded like reversed speech to me, so i reversed the audio file and listened to it

I could then faintly hear "The archive password is "184233965".

I then ran binwalk to extract the archive from the .wav file:
```
sudo binwalk -e sounds_like_stego.wav
unzip 1945A5C.zip
```
Which created a folder named "zipppydidoodaa", containing a flag.txt file

Reading from this file, and inputting the password, i got the flag:

UIACTF{part_3_pressure_pushing_down_on_me_pressing_down_on_you}
