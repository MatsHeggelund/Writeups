*The aliens have captured three of our crew members and is holding them hostage at different locations. Luckily, they managed to send us pictures of their surroundings. Can you figure out where they are being held captive?*

*If I remember correctly, there is a town symbol in the image of the third city.*

*The flag is the cities where these picture was taken, in lowercase, wrapped in UiTHack24{}. If you encouter any acute accent characters (e.g. à) in the city name, replace them with their non-accented counterparts (e.g. a).*

*Example: UiTHack24{city1_city2_city3}*

------

This CTF challenge from the misc category included three images of different locations.

The first city was found by reverse image searching the city1.png. It is an image of the ski jump in Holmenkollen (Oslo).

The second city was found by analyzing the road signs given in the image, and then looking at Google Maps to figure out where E263 and E67 intersected. This was in Tallinn

The third city was found by reverse image searching the unique high-heel shaped flowerbed, along with the PRIOR building in the background. The location was the Slovakian city "Partizànske"

Putting these cities together in the specified flag format, the flag is as follows:

```
UiTHack24{Oslo_tallinn_partizanske}
```

